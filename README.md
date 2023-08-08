# playSMS Installation

Setup User for VPS login and 
Make sure to have user with sudo access
```
sudo adduser jarvis
sudo usermod -aG sudo jarvis
sudo ls /root
su - jarvis
sudo ls /root
```

Perform system update and upgrade
```
sudo apt update && sudo apt upgrade -y 
```

Reboot if necessary , if kernel update
```
sudo reboot
```
Basic Installtion Setup in Ubuntu

### Install Net Tools
```
sudo apt install net-tools -y
sudo systemctl enable ssh
```
Reboot after upgrade is best practice.

### Install Docker
```
sudo apt install -y docker
sudo service docker start
sudo docker pull playsms/playsms:1.4.5
sudo docker run -d -p 80:80 playsms/playsms
```

Run Docker Container

#### Detached Mode (-d)

```
 sudo docker run -d -p 80:80 playsms/playsms 
```

#### Run Live Mode (-d)

```
 sudo docker run -p 80:80 playsms/playsms 
```

### Handelling Error:

```
username@hostname:~$ sudo docker run  -p 80:80 playsms/playsms
docker: Error response from daemon: driver failed programming external connectivity on endpoint trusting_neumann (19dc0ef976296faef4fa1159c52d211cbefe55d83c5281cf2d8bcd5dd122b5a5): Bind for 0.0.0.0:80 failed: port is already allocated.
ERRO[0000] error waiting for container: context canceled
```
Get Container ID
```
sudo docker container ls
```

Kill Running port 
```
sudo docker rm -f 9e5b50704bcc
```

And re-run
```
sudo docker run  -p 80:80 playsms/playsms
```

> Take note of admin password before clearing console.


# 

# Kannel Installation

(It may not work)

```
git clone https://github.com/onlinecity/kannel-docker.git
cd kannel-docker/
sudo apt install docker-compose -y
sudo docker-compose up
```

Link to get status check link for kannel
`https://www.kannel.org/pipermail/users/2010-February/010154.html`

### Working:

```
git clone https://github.com/drfb/kannel-docker
cd kannel-docker
```

Edit config in conf dir
then start with docker compose


### Login to playsms

```
Username : admin
passoword : admin
```

Go to Manage SMSC and Gateway from settings menu

Find `Kannel` in Gateway List then click on edit

Configure all required necessary step until Kannel Bearer box message pop in `Operation tab`

