pipeline {
    agent any
tools {
  git 'Default'
}
    stages {
        stage('SCM') {
            steps {
                git branch: 'master', credentialsId: 'tarun_git', url: 'https://github.com/tarunagni/time-tracker.git'
            }
        }

        stage('Build') {
            steps {
                // Use Maven to build the project
                bat 'mvn clean install'
            }
        }
        
        stage('Deploy') {
            steps {
				// shutdown tomcat
				bat 'D:\\work_dsi\\windows_linux_tomee\\apache-tomee-plus-8.0.5\\bin\\shutdown.bat'
                // Copy the generated WAR file to Tomcat webapps folder
                bat 'copy C:\\Users\\TAI8\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\git_test_new\\web\\target\\*.war D:\\work_dsi\\Middleware\\windows_&_linux_tomee\\apache-tomee-plus-8.0.5\\webapps\\'
				// start tomcat
				bat 'D:\\work_dsi\\Middleware(Tomee_Java)\\windows_&_linux_tomee\\apache-tomee-plus-8.0.5\\bin\\startup.bat'
            }
        }
       
    }
}
