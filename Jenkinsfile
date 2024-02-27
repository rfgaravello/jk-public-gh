pipeline {
    agent any

    stages {
        stage('Cloning git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/rfgaravello/jk-public-gh.git'
            }
        }
        stage('Building Image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('Deploying application') {
            steps {
                sh '''
                # docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
            '''
            }
        }
    }
}
