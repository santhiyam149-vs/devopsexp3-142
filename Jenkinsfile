pipeline {
    agent any

    stages {

        stage('Verify Application Files') {
            steps {
                echo 'Verifying project files...'

                bat 'if exist index.html (echo index.html Found) else (exit /b 1)'
                bat 'if exist style.css (echo style.css Found) else (exit /b 1)'
                bat 'if exist script.js (echo script.js Found) else (exit /b 1)'
            }
        }

        stage('Create Build Artifact') {
            steps {
                echo 'Creating ZIP file...'
                bat 'powershell Compress-Archive -Path * -DestinationPath devopsexp3-142.zip -Force'
            }
        }

        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'devopsexp3-142.zip', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Application Build Successful.'
        }

        failure {
            echo 'Application Build Failed.'
        }
    }
}
