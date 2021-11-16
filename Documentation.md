## Welcome to the Docker Project Documentation Page
## I will be documenting how I installed and ran OpenVAS via Docker.

I started by following the guide on, https://utulsa.hosted.panopto.com/Panopto/Pages/Embed.aspx?id=75912983-0806-47a5-a3ad-acc9018aaec3 as well as following the guide on https://github.com/mikesplain/openvas-docker.
The first step I did was install docker on my VM.
## (sudo apt install docker.io)
Then, I updated and upgraded my machine.
## (sudo apt-get update)
## (sudo apt-get upgrade)
Next, I ensured that docker was running by typing,
## (sudo service docker start)
and checked it using
## (service docker status)
Next, I installed the container using the command
## (sudo docker run -d -p 443:443 --name openvas mikesplain/openvas:9 )
which installs the container and names it openvas by pulling mikesplain/openvas:9 which is the more up to date version of openvas.
Now, I had to wait for openvas to fully install the NVT which is the vulnerability signatures it sees. I checked this by looking into system monitor to check if my CPU was fully being used which means it is still running.
After my CPU usage dropped back down, I knew it was finished installing. 
Then, I began to setup the docker compose by first, editting the docker-compose.yml file 
## (nano docker-compose.yml)
and pasting in the text that was in the github page https://github.com/mikesplain/openvas-docker that I was following and took out everything except the openvas section of the file. I changed the OV_PASSWORD to a password of my choice and then saved and exitted.
![Screenshot from 2021-11-15 19-42-34](https://user-images.githubusercontent.com/29709211/141892254-fdf8286a-4f89-4751-bc6d-2ce123bf380c.png)
Next, I downloaded the Docker compose
## (sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
<img width="755" alt="image" src="https://user-images.githubusercontent.com/29709211/141892345-97d4cadf-f8b3-4407-823c-caf62b0f2a02.png">)
## (sudo chmod +x /usr/local/bin/docker-compose)
And I tested it using
## (docker-compose --version)
which showed me that I succesfully downloaded everything correctly.
Then, I ran it using 
## (docker-compose up -d)
which took a while to run, but eventually finished.
Then, I went to firefox and since my container was installed locally, I typed in the webpage
## (https://localhost/)
I logged into the security assistant using username admin and the password was the same.
Once logged in, I used the task wizard to scan my whole VM which is going to take a very long time. During the scan, I took a bunch of screenshots of my progress and took some screenshots of my results.
![Screenshot from 2021-11-15 19-41-51](https://user-images.githubusercontent.com/29709211/141892527-79ac106e-f16d-4449-84cc-a209ccc59839.png)
![Screenshot from 2021-11-15 19-37-39](https://user-images.githubusercontent.com/29709211/141892533-5d64fe9a-1f0b-4c31-aee3-9837c5a72c85.png)
This was the steps and documentation of my docker project of how to install and run OpenVAS.
