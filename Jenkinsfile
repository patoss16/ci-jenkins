pipeline{
    agent any
    /*tools{
        maven "maven3"
    }*/
    environment {
        SNAP_REPO = "maven-snapshots"
        NEXUS_USER="admin"
        NEXUS_PASS="Benashou1980"
        RELEASE_REPO="ci-release"
        CENTRAL_REPO="maven-central1"
        NEXUS_GRP_REPO="maven-group"
        NEXUSIP = "172.31.41.3"
        NEXUSPORT = "8081"
    }
   stages{
       stage('Fetch code'){
           steps{
               git branch: 'jpac',
               url: 'https://github.com/patoss16/ci-jenkins.git'
           }
       }
       stage('BUILD'){
            steps {
             sh 'mvn install -DskipTests'
            }
        }
        stage('INTERGRATION'){
            steps {
             sh 'mvn verify -DSkipUnitTest'
            }
        }
        stage('UNIT TEST'){
            steps {
             sh 'mvn test'
            }
        }
        stage('Slack it'){
            steps {
                slackSend channel: '#aws-project', 
                          message: 'Build and Tested successfully'
            }
        }
   }
}
