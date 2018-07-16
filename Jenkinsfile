node('master') {
    stage('Preparation') {
        git 'https://github.com/jglick/simple-maven-project-with-tests.git'
        mvnHome = tool 'M3'
    }
    stage('Build') {
        //withMaven(maven: 'M3') {
        //    sh 'mvn -Dmaven.test.failure.ignoe clean package'
        //}
        // Run the maven build
        if (isUnix()) {
           sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
        } else {
           bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
        }
    }
    stage('Results') {
        junit '**/target/surefire-reports/TEST-*.xml'
        archive 'target/*.jar'
    }
}
