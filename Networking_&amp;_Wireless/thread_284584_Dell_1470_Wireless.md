---
title: "Dell 1470 Wireless"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by skierkegaard on 2006-10-25
I am trying to get a wireless connection going on this Dell Inspiron 600m.  

sudo lshw -C network reveals

  *-network:1 DISABLED
       description: Wireless interface
       product: Dell Wireless 1470 DualBand WLAN
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:54:dd:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.22 firmware=Broadcom,05/26/2005, 3.120.27.0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:5

I have gone through and extracted the drivers from the windows .exe and ndiswrapper seems to see it.  However, I cannot get the connection started.  Maybe something to do with link=0?

---

### Post by skierkegaard on 2006-10-25
Any advice is appreciated, even if its not about ndiswrapper.  I'd just really like to get this running.

---

### Post by blink2401 on 2006-11-06
I know it has been a week since you last updated this thread but I have the same network card as you and I was able to get mine to work. Here is what I had to do.

add 'blacklist bcm43xx' to /etc/modprobe.d/blacklist
This is because it was using the broad com 43xx driver and it was not working for my card.

I then installed ndiswrapper, 
apt-get install ndiswrapper-utils

Next I downloaded the windows driver from dell.
unziped the exe and installed the driver with this command
'ndiswrapper -i bcmwl5.inf'

checked that it was installed properly.
ndiswrapper -l

which should display the following if correctly installed.
Installed drivers:
bcmwl5          driver installed, hardware present 

then I ran ndiswrapper -m 

I rebooted so it was using the correct driver.
The card should show up as wlan0 if it worked correctly.

now just set the essid to your routers essid, and use dhclient or manually configure the ip.

You should be all set.

---

### Post by ck-81 on 2006-11-11
hi blink
i followed step by step your istructions but when i ndiswrapper -l
it display:

bcm43xx.cat invalid driver!
bcmwl5 driver present,hardware present

but my w card not works.

maybe caused by bcm43xx that is not blacklisted well?

i wrote it in the blacklist!

tnx for your help

---

### Post by FrodoB on 2006-11-11
Did it work after you blacklisted it?

---

### Post by skierkegaard on 2006-11-12
neither ndiswrapper or fwcutter seemed to work.  I have put that computer's wireless to rest for now.  Maybe I'll give it a more serious run someday.

---

### Post by ck-81 on 2006-11-12
no it didn't work even if i blacklisted the driver

---

### Post by trapman on 2006-11-18
**THIS WORKED FOR ME!!!!!!!!!**

I spent the entire day trying to figure this out and I finally got it to work. I am new to this so please bear with me. Also the process below assumes you know a few things. If you have questions please ask.

Take the wireless card out of the PC or laptop
Reinstall Ubuntu or remove the device. I a newbie so I dont know how to do this
Download the correct driver from here. 
Unzip the driver on Windows box, and then copy it to the Unbuntu box. The entire subdirectory, not just the .inf file
blacklist bcm43xx
Search for and install ndiswrapper -util using Synaptic Package Manager
sudo apt-get install network-manager-gnome
Install driver 'ndiswrapper -i bcmwl5.inf'
ndiswrapper -l
ndiswrapper -m
Reboot

---

### Post by ravyn on 2007-05-02
I know this is an old thread, but I thought I would reply.  I followed this suggestion for my Dell 1470 Wlan card in my Dell Latitude D810 with Ubuntu 7.04.  It worked flawlessly!!!  As soon as I rebooted, my card picked up my wireless and several of my neighbors :) .

Thank you Ubuntu community!!

~ravyn


> **blink2401 said:**
> I know it has been a week since you last updated this thread but I have the same network card as you and I was able to get mine to work. Here is what I had to do.

add 'blacklist bcm43xx' to /etc/modprobe.d/blacklist
This is because it was using the broad com 43xx driver and it was not working for my card.

I then installed ndiswrapper, 
apt-get install ndiswrapper-utils

Next I downloaded the windows driver from dell.
unziped the exe and installed the driver with this command
'ndiswrapper -i bcmwl5.inf'

checked that it was installed properly.
ndiswrapper -l

which should display the following if correctly installed.
Installed drivers:
bcmwl5          driver installed, hardware present 

then I ran ndiswrapper -m 

I rebooted so it was using the correct driver.
The card should show up as wlan0 if it worked correctly.

now just set the essid to your routers essid, and use dhclient or manually configure the ip.

You should be all set.

---

### Post by spudgunner on 2008-03-29
how do you blacklist a the driver?

nevermind

---

