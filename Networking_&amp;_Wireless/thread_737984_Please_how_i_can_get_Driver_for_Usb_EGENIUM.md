---
title: "Please how i can get Driver for Usb EGENIUM"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-03-28
Please how i can get driver for Engenius 108Mbps 802.11g USB 2.0 Wireless Adapter. and how to install in on ubuntu , i wanna to move from microsoft windows to Ubuntu and just this obstacle,,

---

### Post by dstew on 2008-03-28
Post the output of```
lsusb
```so we can see exactly which adapter you have. For the current USB 2.0 adapter, the Windows drivers are [here]("http://www.engeniustech.com/resources/EUB862_362_XPV2.1.zip"). You might be able to use these with ndiswrapper, if there is not open source or restricted driver available. You did check the System --> Administration --> Restricted Drivers Manager already, right?

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-03-28
Ok , my Hardware is Engenius 108Mbps 802.11g USB 2.0 Wireless Adapter  ,the version of ubuntu is  ubuntu-8.04-beta when i post  lsusb the result was
 

yassir@yassir-laptop:~$ lsusb
Bus 005 Device 002: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
yassir@yassir-laptop:~$

now please i want to know how to install thats device on thats version of ubuntu step by step please
with thanx

---

### Post by dstew on 2008-03-28
Did you check in the Restricted Drivers Manager to see if there is a driver available for that device? What Ubuntu version do you have installed?

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-03-29
I have ubuntu-8.04-beta-desktop-i386 but i do not find the restricted device manager when i went  to system then adminstration but no restrict device nanager ,, another prolplem i do not know how to use ndiswrapper to install the windows drivers on ubuntu , and i got these res

yassir@yassir-laptop:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
yassir@yassir-laptop:~$ sudo apt-get install ndiswrapper-common
[sudo] password for yassir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
yassir@yassir-laptop:~$

---

### Post by dstew on 2008-03-29
Sorry, I don't know much about 8.04. I don't know why it couldn't find ndiswrapper. Maybe 8.04 does not use ndiswrapper, or it hasn't been packaged for use yet. Does 8.04 have Synaptic Package Manager? You can look for ndiswrapper in there. Maybe you have to enable a repository (in the Settings tab) to get it.

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-03-29
so do you know why i can not find (restricted device manager),

---

### Post by dstew on 2008-03-29
No. I do not know anything about the GUI of 8.04. Maybe it has a different name, or maybe 8.04 has a different menu structure.

---

