pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            stepes {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Ya acabaset de ver el sitio?'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}