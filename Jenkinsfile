pipeline{
    agent any
    stages{
        stage('Build image'){
            steps{
                script{
                    echo 'Building docker image.....'
                    sh "docker build -t my-app-${BUILD_NUMBER} ."
                }
            }
        }
        stage('Deploy changes'){
            steps{
                script{
                    echo 'Deploying changes......'
                    sh "docker ps -q | xargs -r docker stop"
                    sh "docker run -d -p 3001:3000 my-app-${BUILD_NUMBER}"
                }
            }
        }
    }
}