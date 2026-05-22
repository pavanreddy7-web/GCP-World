pipeline{
    agent any
    environment{
        VM_NAME   = 'jenkins-server'
        ZONE      = 'asia-south1-a'
        PROJECT   = 'project-406aa535-2e75-4c13-869'
        REMOTE_COMMAND = 'cd /home/kotta && javac Hello.java && java Hello'
    }
    stages{
        stage('test'){
            steps{
                bat '''
                  gcloud version
                  gcloud compute zones list
                '''
            }
        }
        stage("run java in vm"){
            steps{
                bat '''
                  ssh %VM_NAME%.%ZONE%.%PROJECT% "%REMOTE_COMMAND%"
                '''
            }
        }
        stage('list'){
            steps{
                bat '''
                  gcloud compute zones list
                '''
            }
        }
    }
}
