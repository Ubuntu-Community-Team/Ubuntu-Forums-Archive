---
title: "Wired Connection Broken, Broadcom!"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by xcitu on 2008-06-17
Hey.
I have a fresh install of Ubuntu 8.04 LTS, and want to get the internet up and going, only wired atm. 
I have plugged my cable into my pc, and using fibernet. 
My card:
Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

I have tried to configure it to DCHP, but with no success. 

What can I do to get my internet working?

If there is anything else you need to know, then tell me what it is and how to do it :)

Thanx in advance!

- X

---

### Post by Vel-Tyno on 2008-06-17
I have a similar problem. But, I am trying to get my wireless connection working.  I also have a:

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Joe

---

### Post by xcitu on 2008-06-17
> **Vel-Tyno said:**
> I have a similar problem. But, I am trying to get my wireless connection working.  I also have a:

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Joe

Hmm, ok, but how did you get your Wired internet to work?

---

### Post by xcitu on 2008-06-17
UPDATE:
Found out that I only have ATI Fire GL driver installed, is it supposed to be like this? How can I get more drivers if thats what I need?
I also found out, after trying some commands in terminal, that I dont got ndiswrapper installed, at all. It doesnt exist. 

How can I get this working?

- X

---

### Post by Ayuthia on 2008-06-17
> **Vel-Tyno said:**
> I have a similar problem. But, I am trying to get my wireless connection working.  I also have a:

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

JoeYou can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754) 
It should work on your card.

---

### Post by Ayuthia on 2008-06-17
> **xcitu said:**
> UPDATE:
Found out that I only have ATI Fire GL driver installed, is it supposed to be like this? How can I get more drivers if thats what I need?
I also found out, after trying some commands in terminal, that I dont got ndiswrapper installed, at all. It doesnt exist. 

How can I get this working?

- X
If you have the Hardy live CD, you can install ndiswrapper.  You should be able to add the CD through Synaptic under Manage Repositories.  If you can't find it, you can also add it by going to the Terminal and typing:
```
sudo apt-cdrom add
```
It will ask you to insert the CD and press enter.  Once that is done:
```
sudo apt-get update
```
That will add the repository list from the CD.  You can then install ndiswrapper-utils-1.9 from Synaptic or from the Terminal:
```
sudo apt-get install ndiswrapper-utils-1.9
```

You can then work with this guide:
[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)
You should not have to do step 2 since the above steps installed ndiswrapper for you.  You will have to find a way to download the Windows driver in step 1 though.

As for your wired connection, I am not for sure about that one.  Have you tried from the terminal:
```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

