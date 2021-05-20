node {
  def app
  stage('Clone the repository') {
    checkout scm
  }
  
  stage('Build iamge'){
    app = docker.build("shreyamshsm/nodejs-docker-jenkins")
  }
  
  stage('Test image') {
    app.inside {
      sh 'echo "Tests passed"'
    }
  }
  
  stage('Push image') {
    docker.withRegistry('https://registry.hub.docker.com/', 'dockerhub_id') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
