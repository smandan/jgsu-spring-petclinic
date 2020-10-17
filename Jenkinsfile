pipeline {
    agent any
//  triggers { pollSCM('* * * * *') }

    stages {
//      have an implicit checkout out

        stage('Build') {
            steps {
                sh "mvn spring-javaformat:apply -Dmaven.test.failure.ignore=true clean package"

            }
        }
    }

    post {
//      If Maven was able to run the tests, even if some of the test
//      failed, record the test results and archive the jar file.
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
