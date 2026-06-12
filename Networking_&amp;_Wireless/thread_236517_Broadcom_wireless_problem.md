---
title: "Broadcom wireless problem"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by dpike619 on 2006-08-14
I have a Broadcom 4306 wireless card on my computer and I'm trying to set it up so that I can use it with NetworkManager.  I've been using [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper") to set it up, and I am able to connect, but it gets a little shaky after I reboot.  The guide says to comment out all of the lines referring to the wireless card in /etc/network/interfaces and I did that, but now when I first boot up the card is not recognized by the NetworkManager or if I do iwconfig.  I can get it to work if I disable the network, do modprobe on the driver and then try to connect.  Has anyone else had a similar problem?  Is there any way I can get the card to be recognized at startup without interfering with Network Manager?

---

### Post by dpike619 on 2006-08-15
Hate to bump my own thread, but I was hoping to get an answer on this one.  It seems like there must be some way to have the modprobe bcm43xx command run at startup before NetworkManager gets going, but I wouldn't know how to do that.  If anyone has any ideas let me know. Thanks.

---

### Post by Darkhack on 2006-08-15
Try adding the module name to /etc/modules or modules.conf or whatever it is called and add your driver to the list if it is not already there.

---

### Post by dpike619 on 2006-08-16
I tried doing that, but it didn't seem to do anything.  I was looking around a bit more and I realized that bcm43xx was listed in /etc/modprobe.d/blacklist, so I commented the line out and now it works perfectly.  Thanks.

---

