pipeline {
  agent any
  environment {
    GITHUB_REPO = "your/repo"
  }
  stages {
    stage('Build') {
      steps {
        // your build steps
      }
    }
  }
  post {
    always {
      script {
        // check if there are any new issues or labels
        def events = checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'repo']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/' + env.GITHUB_REPO + '.git']]]
        for (event in events) {
          if (event.eventName == 'issues') {
            // perform actions for new issue
          } else if (event.eventName == 'label') {
            // perform actions for new label
          }
        }
      }
    }
  }
}
