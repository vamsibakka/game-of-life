pipeline {
    agent {label 'java_11'}
    stages{
        stage ('clone'){
            steps{
            git branch:'master',url:'https://github.com/vamsibakka/game-of-life.git'
        }
    }
    stage ('build') {
        steps{
        sh """ 
        export PATH="/usr/lib/jvm/java-8-openjdk-amd64/bin:$PATH"
        mvn package

        """
    }
    }
    stage ('test'){
        steps{
            junit '**/surefire-reports/*.xml'
        }
    }
    stage ('archvie'){
        steps{
            archiveArtifacts artifacts:'**/target/*.jar'
        }
    }
    }
}