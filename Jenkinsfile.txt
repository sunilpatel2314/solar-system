pipeline {
    agent any

    tools {
        nodejs 'nodejs-version-22.6' // Must match the name in Global Tool Configuration
    }

    environment {
        MONGO_USERNAME = 'rajendra0968jangid'
        MONGO_PASSWORD = 'Hu9RLEvt926c6dYj'
        NODE_ENV = 'development'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                    export MONGO_URI="mongodb+srv://${MONGO_USERNAME}:${MONGO_PASSWORD}@cluster0.wyu84.mongodb.net/solar-system"
                    npm install --no-audit
                '''
            }
        }

        stage('Run the project') {
            steps {
                sh '''
                    export MONGO_URI="mongodb+srv://${MONGO_USERNAME}:${MONGO_PASSWORD}@cluster0.wyu84.mongodb.net/solar-system"
                    npm run start
                '''
            }
        }
    }
}
