pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // This checks for changes every minute
    }

    environment {
        GIT_REPO = 'https://github.com/workrav/live-pop.git' // Replace with your repository URL
        GIT_BRANCH = 'main' // Replace with your branch name
        DEPLOY_DIR = '/var/www/html'
    }

    stages {
        stage('Pull Latest Code') {
            steps {
                script {
                    if (fileExists("${DEPLOY_DIR}")) {
                        dir("${DEPLOY_DIR}") {
                            sh 'git pull'
                        }
                    } else {
                        sh "git clone -b ${GIT_BRANCH} ${GIT_REPO} ${DEPLOY_DIR}"
                    }
                }
            }
        }
    }
}

