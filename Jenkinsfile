pipeline 
{
    agent any
    stages
    {
        stage('Cont download')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/selenium-saikrishna/maven.git'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'download failed from scm', cc: '', from: '', replyTo: '', subject: 'jenkins failed to fetch', to: 'shabervali006@gmail.com'
                    }
                }
            }
        }
        stage('cont build')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh label:'',script: 'mvn package'
                    }
                    catch(Exception e)
                    {
                        mail bcc: '', body: 'download failed from scm', cc: '', from: '', replyTo: '', subject: 'jenkins failed to fetch', to: 'shabervali006@gmail.com'
 
                    }
                }
            }
        }
        stage('cont deploy')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh label: '',script: 'scp /home/ubuntu/.jenkins/workspace/declarativeexample/webapp/target/webapp.war ubuntu@172.31.14.122:/var/lib/tomcat8/webapps/testenv.war'
                    }
                    catch(Exception e)
                    {
                         mail bcc: '', body: 'download failed from scm', cc: '', from: '', replyTo: '', subject: 'jenkins failed to fetch', to: 'shabervali006@gmail.com'

                    }
                }
            }
        }
        stage('cont testing')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
                    }
                    catch(Exception e)
                    {
                       mail bcc: '', body: 'download failed from scm', cc: '', from: '', replyTo: '', subject: 'jenkins failed to fetch', to: 'shabervali006@gmail.com'

                    }
                }
            }
        }
        
    }
    post
    {
        success
        {
            sh label: '',script: 'scp /home/ubuntu/.jenkins/workspace/declarativeexample/webapp/target/webapp.war ubuntu@172.31.8.198:/var/lib/tomcat8/webapps/prodenv.war'
        }
        failure
        {
             mail bcc: '', body: 'download failed from scm', cc: '', from: '', replyTo: '', subject: 'jenkins failed to fetch', to: 'shabervali006@gmail.com'

        }
    }
}
