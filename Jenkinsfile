pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests...'
            }
        }

        stage('Archive Reports') {
            steps {
                writeFile file: 'test-report.txt', text: 'BUILD SUCCESS'
                archiveArtifacts artifacts: '*.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "✅ Branch ${env.BRANCH_NAME} build PASSED"
        }
        failure {
            echo "❌ Branch ${env.BRANCH_NAME} build FAILED"
        }
    }
}