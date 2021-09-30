pipeline {
  agent {label 'slave1'}
  stages {
   
stage ('build'){
      steps{
        sh 'pwd'
        sh 'ls'
        sh 'docker build -t mvnam:latest .'
      }
    }
     stage ('publish'){
      steps{
        sh 'docker tag mvnam:latest sha9880/mymvn:8.0'
        sh 'docker login -u sha9880 -p Tests129$'
        sh 'docker push sha9880/mymvn:8.0'
      }
    }
  stage ('deploy'){
     agent {label 'slave2'}
      steps{
        sh 'docker login -u sha9880 -p Tests129$'
        sh 'docker pull sha9880/mymvn:8.0'
        sh 'docker run -d -p 9000:8080 sha9880/mymvn:8.0'
      }
    }  
  }
}
