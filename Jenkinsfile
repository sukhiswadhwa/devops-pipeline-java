pipeline {
    agent any 
    environment {
        JAVA_VERSION="11"
        DEVOPS_BATCH="AUG2022"
}

}

triggers { 
    pollSCM('* * * * *') 
}

options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '2', artifactNumToKeepStr: '', daysToKeepStr: '1', numToKeepStr: '2')
}

tools {
  jdk 'JDK11'
  maven 'maven386'
}

stages {
    stage( 'checkout' ) {
        steps{
            checkout scm
             }
        }

        stage ( 'Compile' ) {

        steps{ sh 'mvn compile'
            }
        }
}

post {
    always {
        slackSend channel: 'devops' , message: 'BUILD COMPLETED'

        }
    }




}