pipeline {
  agent any

  tools {
    maven 'maven-3'     // Configure this name in Jenkins: Manage Jenkins → Tools
    jdk 'jdk-17'       // Configure JDK 17 in Jenkins
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build & Test') {
      steps {
        sh 'mvn clean test'
      }
    }

    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }

  post {
    success {
      archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      echo 'Build successful 🎉 JAR archived.'
    }
    failure {
      echo 'Build failed ❌ Check test results.'
    }
  }
}
