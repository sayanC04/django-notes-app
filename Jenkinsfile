@Library("Shared") _

pipeline {
    agent { label "vinod" }

    stages {
        stage("hello") {
            steps {
                script {
                    hello("hello guys i am a pipeline")
                }
            }
        }

        stage("Code") {
            steps {
                script {
                    clone("https://github.com/sayanC04/django-notes-app.git", "dev")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "cultivator404")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "cultivator404")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "This is Deploy the Code with compose"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
