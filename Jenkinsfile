pipeline{
 tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
     agent any
	  
	  stages{
	  
	  stage("checkout"){
	   steps{
	   git 'https://github.com/sradhanjali97-sa/repo.git'
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

	nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/myweb.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'com.idream', nexusUrl: '52.66.179.54:8081/repository/maven-releases/', nexusVersion: 'nexus2', protocol: 'http', repository: 'maven-releases', version: '1.5'
	  
  }
	
}
	}
	}
