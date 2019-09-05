pipeline {
	agent {
		docker {
			image 'gradle:latest' 
       		args '-v /root/.gradle:/root/.gradle' 
        }
	}
	
	options {
		skipStagesAfterUnstable()
	}
	
	stages {
		stage("Compile") {
			steps {
				sh "./gradlew compileJava"
			}
		}
		stage("Unit Test") {
			steps {
				sh "./gradlew test"
			}
		}
	}
	post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
        }
    }
}