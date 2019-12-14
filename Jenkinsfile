pipeline {
    agent any


    stages {
        stage('SCM Checkout'){
          git 'https://github.com/surajdhase/jenkins-example'
        }
  }
    {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Apache Maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Apache Maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('install Stage') {
            steps {
                withMaven(maven : 'Apache Maven') {
                    sh 'mvn install'
                }
            }
        }

         stage ('deploy to tomcat') {
             steps {
                 sshagent(['tomcat']) {
                 sh 'scp -o StrictHostKeyChecking=no target/*.jar ec2-user@54.224.108.150:/var/lib/tomcat/webapps/'
      }
             }
   }
}
}
