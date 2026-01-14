pipeline{
  agent any

  stages{

    stage('Stop Old Container') {
      steps {
        bat 'docker rm -f company-1website || exit 0'
      }
    }
    
    stage('Checkout') {
      steps {
        echo 'Fetching source code from github'
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        echo 'Building Docker image'
        bat 'docker build -t company-1website .'
      }
    }
    stage('Run docker container') {
      steps {
        echo 'Running Docker container'
        bat 'docker run -d -p 8070:80 company-1website'
      }
    }
  }
}
