pipeline {
    agent any
 
    environment {
        GIT_REPO = 'https://github.com/DeekshithSN/sample-web-application.git'
    }
 
    stages {
        stage('List Git Branches') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'github-creds',
                    usernameVariable: 'GIT_USERNAME',
                    passwordVariable: 'GIT_PASSWORD'
                )]) {
                    sh '''
                        REPO_URL=$(echo $GIT_REPO | sed "s#https://#https://$GIT_USERNAME:$GIT_PASSWORD@#")
 
                        echo "Available Branches:"
                        git ls-remote --heads $REPO_URL | awk '{print $2}' | sed 's#refs/heads/##'
                    '''
                }
            }
        }
    }
}