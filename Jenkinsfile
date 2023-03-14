pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    

	stage('Build') { 
            steps { 
               withDockerRegistry([credentialsId: "dockerlogin", url: ""]) {
                 script{
                 app =  docker.build("asg")
                 }
               }
           }
    }

	stage('Push') {
            steps {
                script{
                    docker.withRegistry('https://612327965616.dkr.ecr.us-west-2.amazonaws.com', 'ecr:us-west-2:aws-credentials') {
                    app.push("latest")
                    }
                }
            }
    	}
  }
}
