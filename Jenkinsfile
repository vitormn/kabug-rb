pipeline{
    agent {
        docker{
            image 'qaninja/rubywd'
        }
    }
    
    stages{
        stage('Build'){
            steps{
                echo 'Building or Resolve Dependencies!'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                sh 'rm -f Gemfile.lock'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT'){
            steps{
                echo 'Waiting User Acceptance'
                input(message: 'Go to production?', ok: 'Yes')
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp is ready :)'
            }
        }
    }
}