pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/sravani-revuri/PES1UG22CS685_Jenkins']]
                ])
            }
        }

        stage('Build') {
            steps {
                build 'PES1UG22CS685-1'   // Replace with your actual job name
                sh 'g++ main/hello.cpp -o output'  // Compiling your C++ program
            }
        }

        stage('Test') {
            steps {
                sh './output'  // Running the compiled program
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }

    post {
        failure {
            error 'Pipeline failed'  // Post-action for failure handling
        }
    }
}
