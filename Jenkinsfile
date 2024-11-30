pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/your-repo.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy to OpenShift') {
            steps {
                ansiblePlaybook(
                    inventory: 'inventory',
                    playbook: 'deploy.yml'
                )
            }
        }
    }
}
