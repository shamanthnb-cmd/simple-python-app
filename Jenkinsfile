pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Test (CI)') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage('Run App (CD)') {
            steps {
                sh '''
                . venv/bin/activate
                python app.py
                '''
            }
        }
    }
}
