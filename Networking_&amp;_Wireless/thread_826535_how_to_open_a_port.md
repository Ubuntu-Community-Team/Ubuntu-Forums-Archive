---
title: "how to open a port"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by sp.mahapatra on 2008-06-12
hi i m new to ubuntu.I have some doubts pls make it clear.....

1.how to open a port(i want to open the port 22).my networking service is working.
telnet localhost 22 is also working 
But remotely its not working.

2.how to restart a service .instead of giving /etc/init.d/networking restart.

3.how to save the iptables rules.


please anybody do reply me......

Thanks

---

### Post by kevdog on 2008-06-12
Port 22 is open by default -- however you need to make sure there is a listening process on the port -- having an open port without a listening process doesn't do anything -- its not a security threat -- its simply a black hole with no consequences.

Are you trying to install the openssh-server, ie 
sudo aptitude install openssh-server

Next
What service specifically do you want to restart
/etc/init./networking simply refers to networking services --> Do you need a specific service?

3. Save iptables rules:
sudo iptables-save | sudo tee <filename>

An example would be:
sudo iptables-save | sudo tee /etc/firewall_ruleset

---

### Post by cdtech on 2008-06-12
Use the -I flag to set the iptables rule so that it is not after the last rule which is to deny all.

By adding a new rule with -A, you put the new rule after the "deny all" rule. Doing it that way would never get checked.

iptables -I INPUT -p tcp --dport 22 -j ACCEPT

Hope this helps.....

---

### Post by sp.mahapatra on 2008-06-12
> **kevdog said:**
> Port 22 is open by default -- however you need to make sure there is a listening process on the port -- having an open port without a listening process doesn't do anything -- its not a security threat -- its simply a black hole with no consequences.

Are you trying to install the openssh-server, ie 
sudo aptitude install openssh-server

Next
What service specifically do you want to restart
/etc/init./networking simply refers to networking services --> Do you need a specific service?

3. Save iptables rules:
sudo iptables-save | sudo tee <filename>

An example would be:
sudo iptables-save | sudo tee /etc/firewall_ruleset
Thanks,

I have already install openssh-server.nad now i uninstalled it and then again installed.
NOW pls tell me in step by step manner how can i do ssh to other systems or vicevarsa.


plssssssss

---

### Post by kevmitch on 2008-06-12
Can you ping the system you want to ssh to?
```
$ ping <destination ip>
```
(or same command on windows or mac command line)

Are the two machines on the same network or is there a router or firewall somewhere in between?

---

### Post by kevdog on 2008-06-12
Ok, lets just check that port 22 is visible from the outside 

Lets install a port scanner nmap
sudo aptitude install nmap

Now I dont know if you are testing from two different computers, however from the client computer

nmap -p 22 <ip_address_of_server>

The ip address can be a LAN or WAN address, but if using a WAN address, you need to make sure port 22 on the router is port forwarded to the LAN ip address of the server.

Does this make any sense?

Have you generated ssh keys yet (on client):
ssh-keygen -t rsa -b 2048 (or 4096)

---

### Post by Pap3r on 2008-06-12
ssh <username>@<destination ip>

and... Example, my ssh looks like this: ```
ssh pap3r@192.168.1.65
```

---

### Post by sp.mahapatra on 2008-06-12
> **kevmitch said:**
> Can you ping the system you want to ssh to?
```
$ ping <destination ip>
```
(or same command on windows or mac command line)

Are the two machines on the same network or is there a router or firewall somewhere in between?
Thanks,

i solved the prob.

Actually i got the clue from ur ans.

thanks

---

