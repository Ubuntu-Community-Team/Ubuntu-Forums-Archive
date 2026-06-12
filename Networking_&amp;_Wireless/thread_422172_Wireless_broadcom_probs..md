---
title: "Wireless broadcom probs."
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by raichle on 2007-04-24
Hi,

I am trying to get a dell 1370 wlan adapter to work with feisty fawn.  I did some research and saw that this was generally a difficult process and followed all of the directions out there to fix this but i am having no luck,  Here are the details:

root@avenger://# lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

It's "eth1" right now.

here is where I think the problem is:

root@avenger://# sudo ndiswrapper -l
bcmwl5 : invalid driver!
bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


It seems as though the correct driver (bcmwl5) is there but invalid and the alternative driver  (bcmwl5a) is being ignored....

I added this line to /etc/modprobe.d/blacklist:
 
blacklist bcm43xx

Any suggestions?  I am rather new to Linux so please keep it simple

Thanks!

---

### Post by Spoudumen on 2007-04-24
unless you are using a 64bit distro, you should not be using bcmwl5a.inf. that is the 64 driver. remove all drivers, and use bcmwl5.inf. also use the command sudo rmmod bcm43xx. and make sure bcm43xx is actually blacklisted in /etc/modprobe.d/blacklist. next after removing bcmwl5a.inf and installing bcmwl5.inf type sudo ndiswrapper -m  and also sudo modprobe ndiswrapper.  after that you should be all set!!! good luck.

---

### Post by captain semtex on 2007-04-25
I also had problems with my BCM4306 based wireless card (Linksys WPC54GS v1), but the information at [http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902") solved the problems.

Regards

---

### Post by raichle on 2007-04-25
> **Spoudumen said:**
> unless you are using a 64bit distro, you should not be using bcmwl5a.inf. that is the 64 driver. remove all drivers, and use bcmwl5.inf. also use the command sudo rmmod bcm43xx. and make sure bcm43xx is actually blacklisted in /etc/modprobe.d/blacklist. next after removing bcmwl5a.inf and installing bcmwl5.inf type sudo ndiswrapper -m  and also sudo modprobe ndiswrapper.  after that you should be all set!!! good luck.


Sorry if this is a dumb question but how do I remove the drivers?

---

### Post by raichle on 2007-04-25
ok, I followed all the steps in the link and that were given by replies and now I have this:

root@avenger://#ndiswrapper -l
bcmcl5 : invalid driver!

any other suggestions?
\

---

### Post by raichle on 2007-04-25
ok, I removed the driver and reinstalled it per :[http://ubuntuforums.org/archive/index.php/t-82040.html](http://ubuntuforums.org/archive/index.php/t-82040.html)
and now this is what I get:

bcmwl5 : driver installed
device (14E4:4318) present (alternate driver: bcm43xx)

edit: and I have tried rmmod bcm43xx, I just get ERROR: module bcm43xx does not exist in /proc/modules

feel like I have taken a step back....

edit2:  I see it listed in modprobe -l as 
/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

but not in lsmod


edit3: I think thie means that ndiswrapper is running:

lsmod | grep ndiswrapper
ndiswrapper 194608 0 
usbcore 134200 4 ndiswrapper, ehci_hcd, uhci_hcd

---

### Post by raichle on 2007-04-25
well although everything I posted is still true... I am online now using that  wireless card.  Thanks for the help :)

---

### Post by raichle on 2007-04-25
ok, I have now noticed another problem.  The ndiswrapper mod is not loaded by default.  In order to get it to work I have to run:

modprobe -r ndiswrapeper
modproble ndiswrapper 

everytime I reboot in order to connect.

I have run the ndiswrapper -m command but it always says that the alias directive is already there.  Anyone have any suggestions?

---

### Post by captain semtex on 2007-04-25
Have you installed Network Manager (nm-applet)? I added this to my startup group via the Sessions tool from the System/Administration (or maybe it is System/Preferences) menu.

However you will then reach the problem that I am currently at which is how to get the wireless card to automatically connect to the network when I log on. I've been looking at pam-keyring and followed some instructions in various posts but alas... "close but no cigar" :( 

Regards

---

### Post by raichle on 2007-04-25
It's not that I want to automatically connect to the network.  I am unable to connect to any wifi network until I reload ndiswrapper via the commands above

---

### Post by Floppyjoe on 2007-04-25
```
sudo gedit /etc/modules
```
add the word ndiswrapper to this file then save and exit.

---

