---
title: "Ubuntu not seen by Windows PC's"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by torrey881 on 2008-01-09
Hello,

First off I am new to Ubuntu. I have installed 7.04 on an older pc that I own and attached it to my home network. There are four other computers on the network, all running windows xp. My ubuntubox is a wired computer as are two of my windows pc's. The other two windows pc's are wireless. 

I have run into the problem so many other new users have and that is my windows machines do not see Ubuntu. I have dowloaded and installed Samba and set up my login name and password. The Ubuntu sees and access all four of my xp machines just fine. My ubuntu machine also access the internet just fine.  I have set up a folder and shared it on the ubuntu desktop.

I have spent a couple of days pouring through the forums and outside websites. I've found some excellent walk-throughs which I have followed to the letter but to no avail. One thing to note is that my windows network is called PCR instead of the usual "MSHOME". 

I would be glad to submit any logs that might be of use to anyone.....My local network runs on a netgear firewall/printer server. I have turned off all firewalls, both hard and software.

Really at a loss and would love some suggestions....really enjoying ubuntu.

Thanks.................Jeff

---

### Post by metoor30 on 2008-01-09
So, you want to share a folder with your windows XP machines?  Can you post your samba config file (Only include the configuration of the share for now)?

---

### Post by NJC on 2008-01-09
This HOWTO thread suggests an option of setting up a WINS server through samba ... I tried and it was able to see my Ubuntu 7.10 box ONCE from XP (wired though a router). After that, @$#@#$ problems and gnashing of teeth. There's a dizzying amount of samba info available, but often different.
 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by torrey881 on 2008-01-10
Hope this is what you are looking for. The name of my shared folder is "shared ubuntu".


[Shared Ubuntu]
path = /home/jeff/Desktop/Shared Ubuntu
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by torrey881 on 2008-01-10
Thanks I shall look into that work around!!

---

### Post by evanchu on 2008-01-10
I have successfully shared files between Ubuntu and Windows Vista (in both directions).  I wrote down [some notes]("http://www.evanchu.com/linux2").  Read the following topics on that page:
* Windows serve files to Linux
* Linux serves files to Windows

---

