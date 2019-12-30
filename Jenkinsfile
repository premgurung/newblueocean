pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building'
            sh 'mvn -Dmaven.test.failure.ignore clean package '
          }
        }

        stage('stash') {
          steps {
            echo 'stashing the build for later use'
            stash(name: 'build-test-artifacts', includes: '**/target/surefire-reports/TEST-*.xml,target/*.jar')
          }
        }

      }
    }

  }
}