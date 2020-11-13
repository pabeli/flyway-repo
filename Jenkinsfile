pipeline {
    agent { label 'docker' }
    
    stages {
        stage ('info') {
            steps {
                container ('flyway') {
                    script {
                        sh 'flyway info -url=jdbc:mysql://mysql.mysql.svc.cluster.local:3306/devops -user=devops -password=devops2020' 
                    }
                }
            }
        }

        stage ('migration') {
            steps {
                container ('flyway') {
                    script {
                        sh 'flyway migrate -url=jdbc:mysql://mysql.mysql.svc.cluster.local:3306/devops -user=devops -password=devops2020 -locations="filesystem:./migrations" info' 
                    }
                }
            }
        }
    }
}