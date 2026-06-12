---
title: "File sharing between U.S. 7.10, OS X 10.4 and XP"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by vsiege on 2007-12-05
Im not sure where exactly to put this thread so I'm starting here...

I would like to use my Ubuntu system as a file server to my Mac and Windows machines. Below is a detailed list of the LAN setup. All boxes are plugged into the router which then plugs into my modem. 

1. How do I go about using SAMBA to achieve file sharing locally (on my LAN)?

2. How can I remotely connect to my ubunutu machine to share fiels?

Computers Systems on my network:
1x - Ubuntu Server 7.10
with Xfce desktop, LAMP Server, OpenSSH Server, PostgreSQL Database, Print Server and SAMBA
2x - OS X 10.4
2x - MS XP Home Edition

Router:
Netgear

---

### Post by jasmuz on 2007-12-05
Please check out these links, im sure the will be of much help:

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by csat on 2007-12-05
Here we have a step by step on how to configure SAMBA.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by vsiege on 2007-12-06
Thanks for all the windows material.
do you have any os X tutorials? I cant see my os x machine under xubuntu but, i can see xubuntu on my mac.

---

### Post by csat on 2007-12-06
> **csat said:**
> Here we have a step by step on how to configure SAMBA.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

This tutorial is followed by a thread so maybe you could also post there about OS X.

---

### Post by vsiege on 2007-12-06
thanx.. ill give it a try

---

### Post by zorkerz on 2007-12-10
is samba the best way to do this? With no windows machines I would think there should be another way? Im trying to do something a little bit similar

---

### Post by vsiege on 2007-12-10
I installed the 7.10 server edition of Ubuntu, then put the xubuntu desktop on. I could get ubuntu to mount on my mac but not the other way around. So then I installed the Ubuntu desktop and everything changed for both desktops... i could get both to mount, on each system, and for each desktop environment (GNOME and Xfce).

Mac Settings>
System Preferences>Sharing>
Enable....
Personal File Sharing
Windows Sharing
Remote Login (probably dont need this... i just have it on)
FTP Access (probably dont need this... i just have it on)

I used the Root login to make my life easier.... most people will freak out and tell you all the possible things that can go wrong. Its your computer and your choice.

Make a directory on your Ubuntu machine shared... give it the privilages you want... in my case I gave it a group where it could read and write. Now when you go to log into this folder from the mac.... leave all the fields blank and it should mount. from the ubuntu machine: go to places>Network.... and you should see two versions of the mac drive you want... one with a SSH (if you allowed Remote Login) and one with FTP (if you allowed FTP Access). hyou can even find you mac drive under Places>Network>Windows Network>workgroup

Hope this helps... as I have more time i will put together my version of a HOWTO.... that will include how to use different accounts... b/c at the moment i dont have enough time to figure that out... if you find out or need more help get in touch

---

### Post by zorkerz on 2007-12-10
that means you are using samba to share the files?

---

### Post by vsiege on 2007-12-10
actually i have SAMBA installed,, but havent figured out yet how to set up accounts.

FRom MAC: The ubuntu drive is located in Network>Mshome>NameOfUbuntuMachine
Click "Connect..."
It will give you a dialog windows that says" Select the SMB/CIFS shared volume you want to connect to." with a drop down menu just below
Select the drive and click "OK"
then clear out all fields (this will change when I figure out accounts)
Click "OK" and the disk will mount to your desktop

From the ubuntu machine three protocols of the mac machine are picked up under the Places>Network file Browser... SSH, FTP and Windows Network/SMB

Like I said earlier.... for some reason when i put the ubuntu desktop on, this all got almot easier- im not complaining....
I had installed SAMBA and OpenSSH during my original installation... I recommend putting both on

---

