node {
    def resultImage
    def voteImage
    def workerImage
    docker.withRegistry("https://index.docker.io/v1/", "your docker account" ) { 
      stage('Clone repo') {
        checkout scm
      }
      stage('Build result') {
        resultImage = docker.build("your docker account/result", "./result")
      } 
      stage('Build vote') {
        voteImage = docker.build("your docker account/vote", "./vote")
      }
      stage('Build worker dotnet') {
        workerImage = docker.build("your docker account/worker", "./worker")
      }
      stage('Push result image') {
          resultImage.push("${env.BUILD_NUMBER}")
          resultImage.push()
      }
      stage('Push vote image') {
          voteImage.push("${env.BUILD_NUMBER}")
          voteImage.push()
      }
      stage('Push worker image') {
          workerImage.push("${env.BUILD_NUMBER}")
          workerImage.push()
      }
    }
}
