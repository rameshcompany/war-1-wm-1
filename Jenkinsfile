node{
    stage('pulling code from github'){
       echo"git checkout"
    }
    stage('building with maven'){
        sh 'mvn clean install'
    }
    stage('building updated code into docker image'){
        sh 'docker build -t rameshjanaki494/cicdjenkins:1 .'
    }
    stage('pushing updated image to dockerhub'){
        withCredentials([string(credentialsId: 'dockercred', variable: 'dockerhubpassword')]) {
            sh "docker push -u rameshjanaki494 -p ${dockerhubpassword}"
           }
           sh 'docker push rameshjanaki494/cicdjenkins:1'
    }
    stage('attaching node'){
        node(':test1') {
    // some block
}
    }
}
