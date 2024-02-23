pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your version control system (e.g., Git)
                git 'https://github.com/subhanidevops/pipeline.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build your application (e.g., compiling code, packaging)
                echo 'mvn clean package' // Example for Maven build
            }
        }
        
        stage('Test') {
            steps {
                // Run your tests (e.g., unit tests, integration tests)
                echo 'mvn test' // Example for Maven test
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to a staging environment
                // This could involve copying artifacts to a server, containerization, etc.
                echo 'kubectl apply -f staging.yaml' // Example for deploying with Kubernetes
            }
        }
        
        stage('Smoke Test') {
            steps {
                // Run smoke tests against the staging environment
                echo 'npm run smoke-test' // Example for running smoke tests
            }
        }
        
        stage('Deploy to Production') {
            steps {
                // Deploy the application to production if all previous stages passed
                echo 'kubectl apply -f production.yaml' // Example for deploying with Kubernetes
            }
        }
    }
    
    post {
        success {
            // Notify team or perform actions if the pipeline succeeds
            echo 'Pipeline succeeded! Deployed to production.'
        }
        failure {
            // Notify team or perform actions if the pipeline fails
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}

