---
title: "ufw/gufw on the server"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-08
I have a public server.  I want to remove firestarter on the server, and install ufw, and set port 80, specify a different port for ssh, and restrict access to ssh only from a specific port.  

I saw this
[http://ubuntuforums.org/showthread.php?t=1246070](http://ubuntuforums.org/showthread.php?t=1246070)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

I just want to make sure I am on the right path
> 
sudo apt-get remove --purge firestarter

Then, I want to open port 80 to public, and would like to ssh only through a specific IP on the net other than port 22, lets say server IP is 202.54.1.5 and ssh port is 8822
> 
sudo ufw enable
sudo default deny
sudo ufw allow 80/tcp


changed the ssh port to 8822, add a file &#8220;ssh-custom&#8221;, at /etc/ufw/applications.d/ssh-custom
> 
[SSH Custom]
title= SSH Custom port
description=OpenSSH Server Custom port
ports=8822/tcp
> 
sudo ufw allow ssh
sudo ufw allow 8822


I want to restrict access to a single ip or perhaps range of IP for ssh, how do I do that?
assuming 208.80.152.2 is the client, and 202.54.1.5 is the server
> 
sudo ufw allow proto tcp from 208.80.152.2 to 202.54.1.5 port 8822

is that correct?

thank you

---

### Post by wildmanne39 on 2011-06-09
> **007casper said:**
> I have a public server.  I want to remove firestarter on the server, and install ufw, and set port 80, specify a different port for ssh, and restrict access to ssh only from a specific port.  

I saw this
[http://ubuntuforums.org/showthread.php?t=1246070](http://ubuntuforums.org/showthread.php?t=1246070)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

I just want to make sure I am on the right path


Then, I want to open port 80 to public, and would like to ssh only through a specific IP on the net other than port 22, lets say server IP is 202.54.1.5 and ssh port is 8822



changed the ssh port to 8822, add a file &#8220;ssh-custom&#8221;, at /etc/ufw/applications.d/ssh-custom




I want to restrict access to a single ip or perhaps range of IP for ssh, how do I do that?
assuming 208.80.152.2 is the client, and 202.54.1.5 is the server


is that correct?

thank youHi, I dont know about the rest but my book says the remove purge should be
```
sudo apt-get --purge remove firestarter
```

---

### Post by 007casper on 2011-06-09
sudo default deny doesnt do anything; I get sudo: default: command not found.  I guess that was obvious.  Maybe default statement has to be something else.

on the server, I denied, incoming, and outgoing, then did sudo ufw allow 80/tcp.  

If you physically look at the web page from the server, you don't see the images that are connected from other web sites.  However, since port 80 is open, it serves the web page, and if you look at the website from any other computer, you are able to see the linked images on the website. So, it works.

I am assuming sudo ufw allow 80/tcp just serves the website.

Then, I think I am suppose to specify the application, since port 80 can be used by any client application (firefox, wget, etc).

> 
sudo ufw allow &#8220;Apache Full&#8221;  

do I gain extra security by defining the application?

---

### Post by 007casper on 2011-06-09
on a server if you allow port 80 access, is it necessary to specify an application?  should you dedicate an application for extra security?

such as...
```

sudo ufw allow &#8220;Apache Full&#8221;
``` 

thank you

---

