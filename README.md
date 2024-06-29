1.how to write a docker file

cd path of the docket where we need to save the file-to create the path where we need to save the file
mkdir Dockerfilename-to create a directory for docker file
cd Dockerfilename-to change the directory path to docker file 
touch Docketrfilename-to go inside the docker file 
vim Dockerfilename-use to write a docker file or script inside the docker file
inside the docker file -

FROM ubundu(image name from docker hub or any where else)
MAINTAINER sathish pal <gmail.com>
RUN apt-get update
CMD ["echo","hello world"]
cat Dockerfile name-to see the content inside the docker file
docker build path of the docker file or link of the repostry
(docker build . -if we already inside the directory )

2.how to create docket image
docker build -t myimage:1.0 (myimage(image name):1.0(tag for the image for our reference to identify))

3.how to run docker image
docker images-to see all the images that we have
docker run image_id- to run the docker image

4.how to convert the docket image to container
docker run -d --name my_container my_image
DOCKER COMPOSE
This concept is used to use multiple services at a time
1.install docker compose
once we install the docker then the compose will also automatically download 
docker-compose -v  -to see the version of docker compose

2. create the compose file or yaml file
mkdir composefilename
cd dockerfilename
touck docker-compose.yml
ls 
vi docker-compose.yml
yaml file:
version:'2' - used to define the file version * one
services  - service type 
    
    web: -name of the service
      image: nginx  -name of the image
     ports: -used to expose the image to web url we can access from local meachine
          - 8080:80 
    database: -name of the service
       image: redise -name of the image

cat docker-compose.yml

3.check the validaty of docker file
docker-compose config

4.run docker-compose.yml file by command
docker-compose up -d 

5.stop the docker-compse.yml file
docker-compose down

6.to scale the containers
docker-compose up -d --scale database=4

jenkins
basic needs
*jdk
*maven
*docker

build springwood java projcet using docker image and jenkins

1.jenkins->dashboard->manage jenkins->plugin manager->availble plugins
openjdk
docker-docker pipeline-docker build step-cloudbees docker build

2.mange jenkins->global tool configuration->jdk
install automatically->add installer(install from adoptium.net)
jdk->openjdk11
maven
docker->docker from docker.com

sudo usermod -a -G docker jenkins -to see that the user is in docker group
sudo systemctl restart jenkins
jenkins jobs
create job->free style jobs
select jdk8
copy and past git repostry link 
build step-maven as target
docker build and publish-docker repostry link
     registry crediential

with pipeline jobs:
create job-pipeline
pipeline script:
pipeline {
           agent any
           tools {
	    jdk 'openJDK8'
	   manven 'maven'
	}
	stages {
	             stage('SCM') {
		steps{
		        git pipline script
 	                }
	
 	stages {
	             stage('maven build') {
		steps{
		        sh "mvn clear install"
 	                }
	stages {
	             stage('Docker Build & push') {
		steps{
		        docker script {
			sh "docker build -t docker repostry name:tag(any name) ."
			sh "docker push image_name"
 	                }
	}
           }
}
 	
How to run app through docker container

docker run -p 80:8080 docker_image_name:tag of the image
 copy and past the ip of the instance in web and port number
   eg_ip_192.12.15.200:80/docker-java-app/test

eg_ip_192.12.15.200  - ip address of the host meachine or instance
:80                               - port which is mention in jenkins
/docker-java-app         - its a .jar file which will show after the run of docker image
/test                             - command for the test process


Ansible :
1.	Conditionals
2.	Inventory
3.	Playbooks
4.	Handlers
5.	Ad-hoc Commands
