# janus-docker-compose
janus docker compose config file 

1.Install Docker Engine 
/////////////////////////////////////////////////////////////////////////////
sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

//////////////////////////////////////////////////////////////////////////

2.Clone Janus-docker-compose 
//////////////////////////////////////////////////////////////////////////
cd

git clone https://github.com/pondsecret/janus-docker-compose.git

cd janus-docker-compose/

sudo docker compose up 

//////////////////////////////////////////////////////////////////////////

3.Change configuration in janus.plugin.streaming.jcfg
//////////////////////////////////////////////////////////////////////////
sudo docker exec -it <container id> bash

cd 
cd /usr/local/etc/janus/

vim janus.plugin.streaming.jcfg

***Comment all config***
***At rtsp-test comment out all rtsp-test properties (in {} )***
***at url change it to your rtsp link url and save file***

exit 

cd janus-docker-compose/
sudo docker compose restart 
