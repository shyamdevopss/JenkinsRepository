node
{
     /* echo "GitHub BranhName ${env.BRANCH_NAME}"
    echo "Jenkins Job Number ${env.BUILD_NUMBER}"
    echo "Jenkins Node Name ${env.NODE_NAME}"
  
    echo "Jenkins Home ${env.JENKINS_HOME}"
    echo "Jenkins URL ${env.JENKINS_URL}"
    echo "JOB Name ${env.JOB_NAME}" */
    def mavenHome = tool name: "maven3.8.1" 
    stage("Get code from Github")
    {
       git branch: 'development', credentialsId: '6c2156c7-a6a4-4552-a638-245fd7cd8758', url: 'https://github.com/shyamdevopss/maven-web-application.git' 
    }
    stage("Build")
    {
        
     sh "${mavenHome}/bin/mvn clean package" 
    
    }
    stage("Execute Sonarqube Report")
    {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    
    }
    stage("Upload artifact to Nexus")
    {
         sh "${mavenHome}/bin/mvn deploy"
        
    }
    /* stage("Deploy Application to Tomcat")
    {
        sshagent(['90bfa7f9-485b-400c-8904-201a22f5c9d8'])
    
        {
            sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.25.54.29:/opt/apache-tomcat-9.0.41/webapps/"

        }
    }
    stage("Send Email Notification")
    {
        emailext body: '''Regards
Shyam devops''', subject: 'Build is over', to: 'shyam.devopss@gmail.com'
    }
    stage("build properties")
    {
        properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
    } */
}
