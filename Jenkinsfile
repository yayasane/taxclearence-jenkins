pipeline {
  agent any
  tools{
      maven 'maven'
  }
  stages {
    stage('Build') {
      steps {
        sh "mvn clean package -DskipTests"
      }
    }
    stage('Build Docker image') {
      steps {
        sh "docker build -t taxclearence-system:v1 ."
      }
    }
    stage('Deploy') {
      steps {
        sh "docker run --name taxclearence-system -d -p 8080:8080 taxclearence-system:v1"
      }
    }
  }
}
