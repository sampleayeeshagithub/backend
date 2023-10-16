pipeline {
   agent { label 'workstation' }


   stages {

     stage('Download Dependencies'){
       steps {
         sh 'npm install'
       }
     }

     stage('code quality'){
       when {
         allOf {
           expression { env.GIT_BRANCH == "origin/main" }
           expression { env.TAG_NAME != env.GIT_BRANCH }
         }
       }
       steps {
          //sh 'sonar-scanner -Dsonar.host.url=http://172.31.42.81:9000 -Dsonar.login=admin -Dsonar.password=admin123 -Dsonar.projectKey=backend -Dsonar.qualitygate.wait=true'
          echo 'OK'
       }
     }

     stage('Unit Tests'){
       when {
         allOf {
           branch 'main'
         }
       }
       steps {
         echo 'CI'
       }
     }

     stage('Release'){
       when {
         expression { env.TAG_NAME ==~ ".*" }
       }
       steps {
         echo 'CI'
       }
     }

   }
}