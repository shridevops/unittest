pipeline {
  agent any
  environment {
    PATH = '/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/snap/bin:/usr/shar/ant/bin'
  }

  stages {
    stage('Test') {
      steps {
	sh 'ant test'
      }
    }
    stage('Build') {
      steps {
        sh 'ant build'
      }
    }
    stage('Archive') {
      steps {
         archiveArtifacts '**/*.jar'
      }
    }
    stage('Publish_reports') {
      steps {
        junit '**/TEST-*.xml'
      }
    }
    stage('Deploy') {
      steps {
        sh 'cp target/*.jar /tmp'
      }
    }
    stage('Fingerprint') {
      steps {
        fingerprint '**/*.jar'
      }
    }
  }
}

