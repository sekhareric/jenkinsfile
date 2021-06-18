pipeline {
    agent any
    environment {
        PATH="/opt/maven/bin:$PATH"
    }

    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/sekhareric/hello-world.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('deployment') {
            steps {
                sshagent(['tomcat_deploy']) {
                    sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@18.212.220.124:/opt/tomcat/webapps"
}
            }
        }
        
        
    }
}
