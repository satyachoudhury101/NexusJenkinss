pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/satyachoudhury101/NexusJenkinss.git'
	   }
	                  }
	
	   stage("compile"){
	    steps{
		 sh 'mvn compile'
		}
		}
       stage("test"){
	    steps{
		 sh 'mvn test'
		}
		}
	
       stage("package"){
	    steps{
		 sh 'mvn clean package'
                 sh "mv target/*.jar target/myweb.jar"

		}
		}
stage(backup)
		  {
  steps{

	nexusArtifactUploader artifacts: [[artifactId: 'app', classifier: '', file: 'target/myweb.jar', type: 'jar']], credentialsId: 'ID_NexuS', groupId: 'com.idream', nexusUrl: '34.131.245.199:8081/repository/maven-snapshots/', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '1.6-SNAPSHOT'
	  
  }
	
}
	}
	}
