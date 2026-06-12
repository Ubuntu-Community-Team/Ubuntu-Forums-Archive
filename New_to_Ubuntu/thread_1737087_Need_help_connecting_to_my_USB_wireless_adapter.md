---
title: "Need help connecting to my USB wireless adapter"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Rlemontw on 2011-04-23
I am new to Ubuntu and Linux for that matter. Not sure where to start. I have installed Ubuntu along side XP. So XP is where I am able to get here on the net. How can I view available networks and also I am using the 64bit WEP right now because I have an older computer in my network. Under the security I do not see this option, just 128bit. I am not sure if that is the only problem. Can someone help and point me in the right direction?

Thanks in advance! :popcorn:

---

### Post by frup on 2011-04-23
It is not clear to me if you are asking where you can find how to connect to the wireless networks or if you are having a problem with the wireless.

First look at the top right of the screen. One of the applets up there is for networking. If networking is functional, you should be able to find the networks there.

IF it is not we need to troubleshoot.

The first thing would be to load the hardware drivers program in the system menu. It will see if there are any hardware drivers available to install.

After that if that does not fix it you are going to need to open a terminal from applications > accessories > terminal and type lsusb. Copy and paste the results of that command here and we can find out what model wireless it is hopefully and offer assistance on getting it to work.

---

### Post by Rlemontw on 2011-04-23
> **frup said:**
> It is not clear to me if you are asking where you can find how to connect to the wireless networks or if you are having a problem with the wireless.

First look at the top right of the screen. One of the applets up there is for networking. If networking is functional, you should be able to find the networks there.

IF it is not we need to troubleshoot.

The first thing would be to load the hardware drivers program in the system menu. It will see if there are any hardware drivers available to install.

After that if that does not fix it you are going to need to open a terminal from applications > accessories > terminal and type lsusb. Copy and paste the results of that command here and we can find out what model wireless it is hopefully and offer assistance on getting it to work.

Here is what I got:

rlemontw@rlemontw-EL435AA-ABA-SR1720NX-NA610:~$ lsusb
Bus 003 Device 002: ID 03f0:1411 Hewlett-Packard PSC 750
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n
Bus 001 Device 002: ID 03f0:4507 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rlemontw@rlemontw-EL435AA-ABA-SR1720NX-NA610:~$ 

Thanks

---

### Post by Raken on 2011-04-23
hey 

troubelshoot if the probleme still exist try restart U sys



Raken Hargam

---

### Post by Rlemontw on 2011-04-23
Restart did not work. I guess where my problem is not being able to see available networks. I do not even get a flicker from the light on the wireless adapter.

---

### Post by frup on 2011-04-25
You may find this thread relevant 

[http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)

---

### Post by Rlemontw on 2011-04-29
> **frup said:**
> You may find this thread relevant 

[http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)


Thanks, its working now!

---

