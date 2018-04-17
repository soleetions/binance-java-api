pipeline {
  agent any
  tools {
          maven 'Maven 3.5.3'
          jdk 'JDK 8'
  }
  stages {
    stage('Initialize') {
      steps {
        echo 'Test pipeline on checkout'
        sh '''
            echo "PATH = ${PATH}"
            echo "M2_HOME = ${M2_HOME}"
        '''
      }
    }
    stage('Compilation') {
      steps {
          sh 'mvn -Dmaven.test.failure.ignore=true install'
      }
      post {
          success {
              junit 'target/surefire-reports/**/*.xml'
          }
      }
    }
  }
}