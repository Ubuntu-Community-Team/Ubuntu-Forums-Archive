---
title: "openssh_server connection"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by angelus_kit on 2007-07-29
Dear all 

i installed ssh_server on my ubuntu 7.04 server but when i make netstat | grep tcp i don 't see the service port runig port 22

a seek on the ggogle serache for how to install and configuring ssh server but i don't  find any more information 
when i try to strat ssh i have this message 
root@anginux:/etc/init.d# ssh stop
ssh: stop: Name or service not known
root@anginux:/etc/init.d# ssh start
ssh: start: Name or service not known


pelase can you help me hos i cvan to configure my ssh server ?

thank for you help 
Best Regard

---

### Post by Koybe on 2007-07-29
Try 
```
sudo /etc/init.d/ssh restart
```
If it's not working, be sure ssh is correctly installed ```
sudo apt-get install ssh
```

---

### Post by dmizer on 2007-07-29
install ssh server with this command:
```
sudo aptitude install openssh-server
```

now, before testing ports and the like, test if the server is actually working or not.  do this by testing it directly on the 7.04 server like so:
```
ssh your-ubuntu-username@localhost
```
if that works, and it does not work on a second machine, you have a firewall issue.

---

### Post by angelus_kit on 2007-07-30
Dear 

 thank for your help i reinstalled the openssh server  now all work 

thank you 

Best regard

---

