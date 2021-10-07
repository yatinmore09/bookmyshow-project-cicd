pipeline {
  agent any
  environment {
    //adding a comment for the commit test
    MULE_VERSION = '4.3.0'
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }
    stage('Deploy Sandbox') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'bookmyshow-project-cicd'
      }
      steps {
            bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username=yatinmore97 -Danypoint.password=Monalisa@1997 -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
}
}