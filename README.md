# Install-Frappe-ERPNext-V14-in-Docker
Complete Guide to Install Frappe/ERPNext v14 in Docker

Frappe & ERPNext Install (V14) in Docker

complete Guide to Install Frappe/ERPNext in Docker
Pre-requisites

  ca-certificates
  gnupg
  lsb-release                                   
  docker.io             
  Docker Compose                                   
  dbench                                     
  nano                                     

Offical GitHub URL

#Docker
https://www.docker.com/

#Docker Hub
https://hub.docker.com/

#ERPNext
https://github.com/frappe/erpnext

STEP 0 Setup User in Root

echo $USER
su root
nano /etc/sudoers

truser_name ALL=(ALL:ALL) ALL

sudo apt-get update

STEP 1 Install Docker

#(search docker in current apt files)
sudo apt-cache search docker

sudo apt-get install docker docker.io

#(docker group adding)
sudo groupadd docker
sudo usermod -aG docker $USER

#(docker version)
sudo docker -v
#(docker status active (running))
sudo systemctl status docker

#(docker all Containers list)
sudo docker ps -a

#(docker images list local downloads)
sudo docker images

STEP 2 install Docker Compose

sudo apt-get install docker-compose

STEP 3 Install dbench

sudo apt-get install dbench

STEP 4 Pull And Run The ERPNext in Docker

#(search docker hub image files)
sudo docker search erpnext14

#(pulling docker hub image files to local system)
sudo docker pull sankarprakash/erp14

sudo docker images

sudo docker volume create ERPNextDB

sudo docker volume create ERPNextAPP

sudo docker run -itd -p 4080:80 --privileged=true -v ERPNextDB:/var/lib/mysql -v ERPNextAPP:/home/frappe/frappe-bench/sites --name ERPNext14 sankarprakash/erp14:v1.2

Run The IP and stup Your ERPNext

sudo docker ps

http://0.0.0.0:4080 
####(or) 
http://localhost:4080
