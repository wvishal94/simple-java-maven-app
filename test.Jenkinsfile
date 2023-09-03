pipeline {
    agent any
    stages {
        stage('Test Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test Me') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Test Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
