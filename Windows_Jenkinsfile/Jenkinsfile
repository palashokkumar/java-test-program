pipeline{
    agent{
        label 'master'
    }
    options{
        timestamps ()
        disableConcurrentBuilds()
    }
    triggers{
        pollSCM '* * * * *'
    }
    stages{
        stage('Checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'vivek-ssh', url: 'git@github.com:vivektrivedi-123/java-test-program.git']]])
            }
        }
        stage('Build'){
            steps{
                bat 'mvn clean install'
            }
        }
        stage('Deploy'){
            steps{
                bat 'xcopy "C:\\Program Files\\Jenkins\\workspace\\mvn-pipeline\\web\\target\\time-tracker-web-0.5.0-SNAPSHOT" "C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps "/b/v/y'
            }
        }
    }
}
