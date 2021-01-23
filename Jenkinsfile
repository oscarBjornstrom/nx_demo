
pipeline {
    agent any
     triggers {
        githubPush()
    }
    tools {nodejs "node 15.6.0"}
    stages {
        

        stage('build') {
            steps {
                sh 'npm --version'
                sh 'npm install'
                sh 'npm list'
            }
        }

        stage('lint') {
            steps {
                sh 'npm run nx -- run-many --target=lint --all'
            }
        }
        stage('test') {
            steps {
                sh 'npm run nx -- run-many --target=test --all'
            }
        }

        stage('test affected') {
            steps {
                sh 'npm run "nx affected --target=test --base=master~1 --head=master"'
            }
        }

        
       
    }
}