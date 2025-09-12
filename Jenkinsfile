pipeline{
	agent any
	stages{
	    stage('checkout'){
	        steps{
                echo "Cloning repo"
                git url:"https://github.com/vaishnavikarra/Week-8-DJ.git",
                branch:'master'
	        }
	    }
	    stage('Build'){
	        steps{
                echo "Build Docker Image"
                bat "docker build -t mywebapp ."
	        }
	    }
	    stage('Run'){
	        steps{
                echo "Run application in Docker Container"
                bat "docker rm -f mycontainer || exit 0"
                bat "docker run -d -p 5001:5001 --name mycontainer mywebapp"
	        }
	    }
	}
	post{
	    success{
	        echo 'Pipeline completed successfully!'
	    }
	    failure{
	        echo 'Pipeline failed.Please check the logs'
	    }
	}
}

