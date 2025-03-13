pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                          branches: [[name: '*/main']],
                          userRemoteConfigs: [[url: 'https://github.com/Hamhunter23/PES1UG22CS215_Jenkins.git']]])
            } // <- This was missing!  VERY IMPORTANT.
        } // <- and this one

        stage('Build') {
            steps {
                sh 'g++ -o PES1UG22CS215-1 main.cpp' // Compiles C++ file
            }
        }

        stage('Test') {
            steps {
                sh './PES1UG22CS215-1' // Runs the compiled file
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the application..."
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed' // Post action in case of failure
        }
    }
}
