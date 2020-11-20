
node {
    
    def app
 
    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }
 
    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("teomaik/nodeapp")
    }
 
    stage('Test image') {

        app.inside {
            echo "Tests passed"
        }
    }
 
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
    }
}
