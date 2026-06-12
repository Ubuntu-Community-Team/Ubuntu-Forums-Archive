---
title: "Request for help in setting up remote ssh access"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by jyper on 2008-07-01
Could I get some help on how to set up remote ssh and ssh -x access to my computer. I have installed openssh client and server and can ssh to  localhost. I have a host name but no domain name.

Thank you
Roman Taycher

---

### Post by Waappu on 2008-07-01
Hi

See if you find answer here
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by jyper on 2008-07-01
Sorry it does not help me I know some(small piece) of that and probably don't need to know the rest just yet. All I'm trying to do is to be able to ssh into my system. I don't understand domain or host name very well but I do have a host name. I can ssh using localhost or from my system to itself using the ifconfig generated eth0 inet addr, but if I try to test it from a remote box sshing into my school account and then trying to ssh back into my local box it doesn't work (noting happens you just wait for the process to respond but it doesn't).

---

### Post by Waappu on 2008-07-01
Hi

You can connect using IP address e.g.
```
ssh username@192.255.255.1
```

And of course ssh port need to be open in router

---

### Post by jyper on 2008-07-01
I did try to connect like that. but how do you check if the ssh port is open or closed in router

---

### Post by Waappu on 2008-07-01
Hi

What router or modem you have ?

---

### Post by jyper on 2008-07-01
Dlink wireless router(wired connection to computer) , Arris Modem

---

### Post by Waappu on 2008-07-01
Hi

Ok, I do not know much about those. See manuals about port foward

---

### Post by Vishal Agarwal on 2008-07-01
what is the ssh port ? if it is not changed by default it should be 22. 

use the command
 > ssh -X hostname or IpAddress -l loginname -p portno -v 

this -v will display all the connectivity in verbose mode. U will be able to see all the processing done by ssh. Hope it should work.

Vishal Agarwal

---

### Post by Vishal Agarwal on 2008-07-01
Sorry,

In order to access it from outer world u need to open that user to logon using ssh. otherwise when ever u will try to login remotely it will drop your access. To do so u need to allow the user into /etc/ssh/sshd_config.

ps -> sshd_config not the ssh_config.

search the line Allowusers and put the login name there.restart ssh service.

I hope it should work.

Vishal Agarwal

---

### Post by jyper on 2008-07-01
Now I'm trying to get a static connection so I can get the router to open port 22, but anytime I try to enter a static ip connection in wireless settings I fail, anyone know how this works(I personally know next to nothing about it)?

---

### Post by Vishal Agarwal on 2008-07-02
Router has no role in connectivity. what exactly u want to do, i am not clear.

---

### Post by kevdog on 2008-07-02
Log into your router:

[http://192.168.1.1](http://192.168.1.1)

or 

[http://192.168.0.1](http://192.168.0.1)

Im guessing on the numbers.  Go to the port forwarding section (may have to hunt and peck for it.  And then port forwad port 22 to your client -- Ive included a screenshot for my dlink router -- in my setup I port forwarded port 2222 -- notice its the only thing checked in the list:

---

