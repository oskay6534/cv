pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[url: 'https://github.com/oskay6534/TRT.git']]
                )
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    docker.build("final2:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                    docker.image("final2:${env.BUILD_NUMBER}").run("-d -p 8095:8080 --name adamsinn")
                }
            }
  }
}

}