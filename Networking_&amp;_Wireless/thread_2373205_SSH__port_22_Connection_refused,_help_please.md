---
title: "SSH  port 22: Connection refused, help please"
date: 2017-10-04
forum: Networking &amp; Wireless
---

### Post by pibil1 on 2017-10-04
Greetings Ubuntuforums 

Please I need help. I'm using Lubuntu 17.04, I tried to copy a file using "scp" remotely through ssh but logged in the host computer, not local. Ater that when I try to login via ssh I get this error  "connect to host foobar port 22: Connection refused". 

Things that work:
ssh localhost indeed works

ssh host in another PC through the same router works

Things that haven't worked:
sudo apt-get remove openssh-client openssh-server
sudo apt-get install openssh-client openssh-server
sudo ufw allow 22
ssh -p 22 foo@bar
ssh foo@IP
Going to /etc/ssh/sshd_config and setting "PermitRootLogin yes"
sudo rm /etc/ssh/sshd_config > sudo apt-get purge openssh-server > sudo apt-get install openssh-server
sudo iptables -L > sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
/etc/init.d/ssh restart and  service ssh restart
rm -rf /root/.ssh/*
/etc/init.d/ssh restart  
sudo service ssh restart
Changed /etc/ssh/sshd_config, change Port 22 to Port 2222

Please anybody can help me?, I've donde almost everything I found on google.

Thank you :D

---

### Post by TheFu on 2017-10-04
NEVER allow remote root.  There are always better answers.

Did you allow a port in at the router?

What do the log files show?  Always check the logs on the:
a) client
b) server
c) router

I like to have the router do port-translation, so I ssh in on port 63023 when using the WAN router interface and have that forwarded to the server's 22/tcp port.  Makes setting up my ~/.ssh/config file nicer too.  I use a different hostname for the WAN connection vs from the LAN.

Might help: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by pibil1 on 2017-10-08
OK apparently I was in host's jail. Thank you.

---

