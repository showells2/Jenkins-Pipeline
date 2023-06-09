pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Building using Git ..."
            }
        }
        stage("Test"){
            steps{
                echo "Unit and Integration testing using Hudson Selenium Plugin ..."
            }
            post{
                always{
                    emailext(
                        body: "Status: Success, Test log attached!",
                        attachLog: true,
                        subject: "Test Status Email",
                        to: "sebastianhowells03@gmail.com")
                }
            }
        }
        stage("Code analysis"){
            steps{
                echo "Analysing code with Checkmarx ..."
            }
        }
        stage("Security scan"){
            steps{
                echo "Running security scan using Snyk security ..."
            }
            post{
                always{
                    emailext(
                    to: "sebastianhowells03@gmail.com",
                    subject: "Security Status Email",
                    body: "Status: Success, Security scan log attached!")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying to AWS EC2 instance ..."
            }
        }
        stage("Integration tests"){
            steps{
                echo "Running integration tests ..."
            }
        }
        stage("Complete"){
            steps{
                echo "Completed."
            }
        }
        stage("Deploy to production"){
            steps{
                echo "Deploying to AWS EC2 production server ..."
            }
        }
    }
}
