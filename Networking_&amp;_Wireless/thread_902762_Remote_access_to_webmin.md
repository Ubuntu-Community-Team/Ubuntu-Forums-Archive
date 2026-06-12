---
title: "Remote access to webmin"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by damo12 on 2008-08-27
Please excuse me if this has already been posted elsewhere.  I am pretty new to Linux and have setup up a server using Ubuntu 8.04 with webmin 1.420 running on it.  I can access it from within my network fine and carry out pretty much anythin I want.

What I wouod like to do is access this server from a remote location ie over the internet most likely on a computer running Windows.

From what I can gather I need to use a DNS server and SSH but that is way beyond my limited knowledge.  I would really appreciate it if anyone can point me in the right direction ie another post I've missed or a step by step guide.

Thanks in advance,

Damo

---

### Post by SpaceTeddy on 2008-08-27
right-o...lets get on the job. I think your problem is not really how to setup ubuntu (as you said, everything works already - webmin is up and running and can be access on the local lan). I think your problem is understand the concept of inbound connections to a server and tunneling ports... i'll try to explain it in a nutshell (as i am too lazy to start googling for good tutorials)

Ok - this is the setup i am going to look at for the connection:

Computer <---> home-router1(NAT) <---> Internet <---> home-router2(NAT) <---> Server

You want a connection from Computer to server through all these other things. Well - this is not possible like this. First thing to do is to enable port forwarding on home-router2 (the one in front of the Server). In fact, you want to forward port 22. Why 22 ? well, because that is the ssh port which we are going to utilize. 
But to be able to test this better, it would make sense to have the ssh server up and running and being able to connect internally. So, firstly, install the openssh-server:
```
sudo apt-get install openssh-server
```
once that is up, try to access the server via ssh. once that works internally, try to setup the port forwarding on the router and then try to access the server from the internet (you will need to know your external ip for that - you can find it out [[COLOR="Blue"]here[/COLOR]]("http://whatismyipaddress.com/")). Don't try from your internal network to access that address - it will not work as most home-routers do not forward internal traffic. You will need to do this from the internet. 

Ok... so now you should have an accessable ssh-server from the internet. The next step is to get hostname that always points to your server (as your external ip will most likely change every 24h). Explaning that is a little beyond the scope, but search google for setting up dyndns.org or no-ip.org in ubuntu. there is plenty of documentation out there about it. I personally use no-ip.org...

Hopefully you have the name now - now the last step - forwarding the port. For that, you connect to the ssh server with port forwarding enabled... in linux the command would be:
```
ssh user@myserver.no-ip.org -L 10000:localhost:10000
```
This connects to your server (name is myserver.no-ip.org - change this to your real name or your ip) with the username user. The -L bit is the crutial port. It forwards the localport so your server and then connects to the localhost there on port 10000. Setting it up like this, and then logging into the remote machine. Just leave the console after you have logged in and open a browser... and try to connect to localhost:10000 - that should work. 

I know i did not explain everything... but i hope that is the hint in the right direction... hope it helps :)

---

### Post by damo12 on 2008-08-29
Thanks for the guidance space teddy, this has been running for 24 hours or so now and works perfectly.

Damo12

---

### Post by rgotten on 2008-10-12
i am trying to do something similar, and have look imto hamachi. Do you know if hamachi can be use to be able to connect to the server and use webmin?

---

### Post by SpaceTeddy on 2008-10-13
hamachi can be used to do this - all you need is a direct connection from one point to another to access webmin. You can accomlish this by port forwarding (DNAT), by ssh port forwarding (as described above) or by any VPN that both (the server and the client) connect to. 

A point you might want to take into consideration is that if you use hamachi, you might give the people running hamachi a way to bypass your firewall... 

hope it helps :)

---

### Post by iPower-X2 on 2009-07-12
> **SpaceTeddy said:**
> right-o...lets get on the job. I think your problem is not really how to setup ubuntu (as you said, everything works already - webmin is up and running and can be access on the local lan). I think your problem is understand the concept of inbound connections to a server and tunneling ports... i'll try to explain it in a nutshell (as i am too lazy to start googling for good tutorials)

Ok - this is the setup i am going to look at for the connection:

Computer <---> home-router1(NAT) <---> Internet <---> home-router2(NAT) <---> Server

You want a connection from Computer to server through all these other things. Well - this is not possible like this. First thing to do is to enable port forwarding on home-router2 (the one in front of the Server). In fact, you want to forward port 22. Why 22 ? well, because that is the ssh port which we are going to utilize. 
But to be able to test this better, it would make sense to have the ssh server up and running and being able to connect internally. So, firstly, install the openssh-server:
```
sudo apt-get install openssh-server
```once that is up, try to access the server via ssh. once that works internally, try to setup the port forwarding on the router and then try to access the server from the internet (you will need to know your external ip for that - you can find it out [[COLOR=Blue]here[/COLOR]]("http://whatismyipaddress.com/")). Don't try from your internal network to access that address - it will not work as most home-routers do not forward internal traffic. You will need to do this from the internet. 

Ok... so now you should have an accessable ssh-server from the internet. The next step is to get hostname that always points to your server (as your external ip will most likely change every 24h). Explaning that is a little beyond the scope, but search google for setting up dyndns.org or no-ip.org in ubuntu. there is plenty of documentation out there about it. I personally use no-ip.org...

Hopefully you have the name now - now the last step - forwarding the port. For that, you connect to the ssh server with port forwarding enabled... in linux the command would be:
```
ssh user@myserver.no-ip.org -L 10000:localhost:10000
```This connects to your server (name is myserver.no-ip.org - change this to your real name or your ip) with the username user. The -L bit is the crutial port. It forwards the localport so your server and then connects to the localhost there on port 10000. Setting it up like this, and then logging into the remote machine. Just leave the console after you have logged in and open a browser... and try to connect to localhost:10000 - that should work. 

I know i did not explain everything... but i hope that is the hint in the right direction... hope it helps :)




hey i tryed doing that but it is not working it keeps saying 
"ssh: connect to host agland-williams.homelinux.org port 22: Connection refused

how to i fix this :confused:

---

