pipeline {
    agent any

    stages {
        stage('Build Frontend') {
            steps {
                script {
                    dir('frontend') {
                        sh 'docker build -t frontend:latest .'
                    }
                }
            }
        }

        stage('Build Backend') {
            steps {
                script {
                    dir('backend') {
                        sh 'docker build -t backend:latest .'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'docker-compose down'
        }
    }
}
