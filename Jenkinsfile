pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/uv-uv/uvrepo1', branch: 'master', credentialsId: 'e234132d-1f05-48b8-86a5-11c192e06f34')
        sh '''sudo docker build -t yuvaraj001/jenkinsrepo1:ocean1 .
sudo docker push yuvaraj001/jenkinsrepo1:ocean1'''
      }
    }

    stage('Deploy ') {
      parallel {
        stage('Deploy Dev') {
          steps {
            sh '''sudo docker rm -f $(sudo docker ps -aq) || true
sudo docker run -d -p 7777:80 --name con1 yuvaraj001/jenkinsrepo1:ocean1'''
          }
        }

        stage('Deploy QA') {
          steps {
            echo 'I am in QA stage'
          }
        }

      }
    }

  }
}