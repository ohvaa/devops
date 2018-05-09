pipeline {
    agent any
    environment { 
        imageName = "nootiew/hello-nginx"
    }
    stages {
        stage("Prepare"){
            steps {
                echo "Hello World"
            }
        }
        stage("check version"){
            steps {
                sh "docker --version"
                // sh "cat /home/jenkins/.docker/config.json"
            }
        }
        stage("deploy"){
            steps {
                sshagent(['uat-server']) {
                    sh "ssh -o StrictHostKeyChecking=no core@167.99.237.229 docker pull sommaik/hello-nginx"
                }
            } 
        }
        // stage("push image"){
        //     steps {
        //         script{
        //             docker.withRegistry(
        //                 'https://registry.hub.docker.com', 'docker-id'
        //             ) {
        //                 sh "docker build -t ${imageName} ."
        //                 sh "docker tag  ${imageName} ${imageName}:1.${env.BUILD_NUMBER}"
        //                 sh "docker push ${imageName}"
        //             }
        //         }
        //     }
        // }

    }
}

