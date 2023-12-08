pipeline {
    agent any
    tools {
        maven 'maven_3_9_6'
    }
    stages {
        stage('Build Maven') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sayemmy007/devops-automation']])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image') {
            steps {
                script {
                    bat 'docker build -t imrandockerhub007/devops-integration .'
                }
            }
        }
        stage('Push image to Hub') {
            steps {
                script {
                        
                        bat 'docker login -u imrandockerhub007 -p BlackHole@007'
                        bat 'docker push imrandockerhub007/devops-integration'
                    }
            }
        }
    }
}
