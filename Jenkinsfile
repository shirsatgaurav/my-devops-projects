pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t myapp:${BUILD_ID} .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                docker run -d -p 80:80 --name myapp myapp:${BUILD_ID}
                '''
            }
        }
    }
}
