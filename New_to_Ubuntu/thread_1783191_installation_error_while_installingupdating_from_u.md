---
title: "installation error while installing/updating from universal reppository"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by kiran_viswm on 2011-06-15
am getting error while trying to install or update using synaptic package manager or through terminal..
error is like this:

" W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-mysqldb/python-mysqldb_1.2.2-10build2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-mysqldb/python-mysqldb_1.2.2-10build2_i386.deb)
  Could not connect to 172.16.0.254:8080 (172.16.0.254), connection timed out


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-dbg_2.7.1-5ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7-dbg_2.7.1-5ubuntu2_i386.deb)
  Unable to connect to 172.16.0.254:8080:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-dbg_2.7.1-0ubuntu5_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-dbg_2.7.1-0ubuntu5_all.deb)
  Unable to connect to 172.16.0.254:8080:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-mysqldb/python-mysqldb-dbg_1.2.2-10build2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/python-mysqldb/python-mysqldb-dbg_1.2.2-10build2_i386.deb)
  Unable to connect to 172.16.0.254:8080:

"

this is the error when i tried to install a python module(just as an example)

---

### Post by Rubi1200 on 2011-06-16
Hi and welcome to the forums :-)

Are you still experiencing problems with this?

Open a terminal and run this command:

```
sudo apt-get update
```

If there are errors, please post them here.

---

### Post by kiran_viswm on 2011-06-18
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Are you still experiencing problems with this?

Open a terminal and run this command:

```
sudo apt-get update
```

If there are errors, please post them here.
It is showing the message 
"0% [Connecting to 172.16.0.254 (172.16.0.254)] [Connecting to 172.16.0.254 (172"
for very long time. Actually once i setup a connection with this address and later deleted it. what to do? :(

---

### Post by wildmanne39 on 2011-06-18
> **kiran_viswm said:**
> It is showing the message 
"0% [Connecting to 172.16.0.254 (172.16.0.254)] [Connecting to 172.16.0.254 (172"
for very long time. Actually once i setup a connection with this address and later deleted it. what to do? :(Hi, it looks like you are having trouble connecting to the server, I clicked on the links you provided and I can download them, is your internet connection working properly? You might try again maybe the server was down, but it is working right now. Is there any other error messages you are getting?

---

### Post by kiran_viswm on 2011-06-18
$ sudo apt-get update

this is the error i get


Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
  Unable to connect to 172.16.0.254:8080:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 172.16.0.254:8080:
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
  Unable to connect to 172.16.0.254:8080:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 172.16.0.254:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease                               
  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease                       
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
  Unable to connect to 172.16.0.254:8080:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg
  Unable to connect to 172.16.0.254:8080:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg
  Unable to connect to 172.16.0.254:8080:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease  
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease  
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease  
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  Unable to connect to 172.16.0.254:8080:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  Unable to connect to 172.16.0.254:8080:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  Unable to connect to 172.16.0.254:8080:
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/titheum/equinox/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/titheum/equinox/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Failed to fetch [http://ppa.launchpad.net/titheum/equinox/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/titheum/equinox/ubuntu/dists/natty/Release.gpg)  Unable to connect to 172.16.0.254:8080:

W: Some index files failed to download. They have been ignored, or old ones used instead.


:confused:

---

### Post by dFlyer on 2011-06-18
Looks like your internet connection is not working. Are you using wifi or are you hard wired?

---

### Post by ranatanveer on 2011-06-18
Yes connectivity issu...

---

### Post by Jarramundi on 2011-06-18
Sounds like you haven't got the right repositories?

what do you have in /etc/apt/sources.list ?

You could try:

```
sudo add-apt-repository "deb "http://archive.canonical.com/ natty partner"
```

and then ```
sudo apt-get update
```

See if that helps?

---

### Post by kiran_viswm on 2011-06-19
It is not connectivity issue, am able to browse. Problem is it is checking from wrong ip (i guess so).


kvm@Excaliber:~$ sudo add-apt-repository "deb "http://archive.canonical.com/ natty partner"
> 
> 
> 

this is what i get, and it remains there untill i press keyboard interrupt ctrl+c.

---

### Post by wildmanne39 on 2011-06-19
> **kiran_viswm said:**
> It is not connectivity issue, am able to browse. Problem is it is checking from wrong ip (i guess so).


kvm@Excaliber:~$ sudo add-apt-repository "deb "http://archive.canonical.com/ natty partner"
> 
> 
> 

this is what i get, and it remains there untill i press keyboard interrupt ctrl+c.Hi, thats because it is waiting for you to enter you password that you setup when you installed ubuntu. Can you click on the links that you posted above and it lets you download it that way? if so try what was mentioned in the above post.

---

### Post by kiran_viswm on 2011-06-20
hi !!!!!1
i finally figured out the problem. i once  changed the proxy typing
export HTTP_proxy="username:password@172.16.0.254:8080" .
How to change bit back to my broad band connection??

---

