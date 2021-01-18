pipeline {
    agent any
        stages{
            stage('Git Checkout'){
                steps{
                    git 'https://github.com/salgarsprabu/parking_frontend.git'
                }
            }
            stage('Build') {
                steps{
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm audit fix'
                }
            }
            stage('Deploy'){
                steps{
                    sh 'cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.31/webapps'
                    sh 'curl -u admin:admin http://35.192.17.97:9081/manager/reload?path=/build'
                }
            }
            }
        }
