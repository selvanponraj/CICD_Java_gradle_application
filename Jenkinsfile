pipeline{
    agent any
    stages{
        stage("sonar quality check"){
            agent{
                docker {
                    image 'openjdk:11'
                    args '-e SONAR_USER_HOME=/home/sponraj/.jenkins/workspace/java_grade_application@2/.sonar'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                        sh 'chmod +x gradlew'
                        sh 'env'
                        sh './gradlew sonarqube --stacktrace'
                    }
                }
            }
        }
    }
}