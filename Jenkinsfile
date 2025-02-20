@Library("fdg_parent@release/5.0") _

node('java17-buildah') {

    container("java") {

        stageCheckout()

	    stageCompile()

	    stageTest()

    }

}

void stageCheckout() {
	stage('checkout') {
        checkout scm
	}
}

void stageCompile() {
    stage('compile') {
        sh "mvn -U -B clean test-compile"
    }
}

void stageTest() {
    stage('test') {
        sh "mvn -U -B -Dmaven.test.failure.ignore=true -Dmaven.javadoc.skip=true test"
        junit '**/target/surefire-reports/**/TEST-*.xml'
    }
}
