# 20065334_repo
final courseword

docker  run  -it  --name  puppetclient1 -h puppetclient1.localdomain  ubuntu:18.04  /bin/bash 

//actual cmd to run

docker  run  -it  --name  puppetclient1 -h 20065334-websvr.localdomain  ubuntu:18.04  /bin/bash 



//
apt-get install curl wget vim iputils-ping net-tools openssh-server 


wget --content-disposition 'https://pm.puppetlabs.com/puppet-agent/2021.5.0/7.14.0/repos/deb/bionic/puppet7/puppet-agent_7.14.0-1bionic_amd64.deb' 

 dpkg -i puppet-agent_7.14.0-1bionic_amd64.deb 
 
 
 docker commit puppetclient1 puppetclient-image 
 
 //
 docker commit puppetclient1 20065334-websvr
 
 //
 
 docker network create --subnet=192.168.100.0/24 customnetwork 
 
 //
 docker network create --subnet=192.168.20.0/24 customnetwork 
 
 
 
 
 //
 
 docker run -d  --network customnetwork --privileged -h “puppetclient1.localdomain” --name puppetclient1  --add-host “sddo-vm:172.20.113.92”  --ip “192.168.100.3” puppetclient-image /sbin/init 

172.20.113.92  # puppet master


//
docker run -d  --network customnetwork --privileged -h “20065334-websvr.localdomain” --name 20065334-websvr --add-host “sddo-vm:172.20.113.92”  --ip “192.168.100.3” puppetclient-image /sbin/init 





docker network inspect customnetwork 

root@puppetclient1: 
cat /etc/hosts

172.20.113.92   sddo-vm
192.168.20.50   20065334-websvr.localdomain


root@puppetclient1: 
 vim /etc/puppetlabs/puppet/puppet.conf
 
 //add
 certname = 20065334-websvr.localdomain
 server = sddo-vm
 
 //
 cd /opt/puppetlabs/bin
 ./puppet
 
 ./puppet agent --test
 
 
 
 /opt/puppetlabs/bin/puppet agent -t
 
 
 //
 on the server node 
 
 
 /opt/puppetlabs/bin/puppetserver ca list --all
 
  /opt/puppetlabs/bin/puppetserver ca sign --all
 
 
 //
 on client
 
   /opt/puppetlabs/bin/puppet agent –t
  
  
  
  
    nano ~/.bashrc
    
    export PATH=$PATH:/opt/puppetlabs/bin 
    
    .  ~/.bashrc
    
    echo $PATH
    
     puppet agent -t
     
     
     
   
   
  
  

