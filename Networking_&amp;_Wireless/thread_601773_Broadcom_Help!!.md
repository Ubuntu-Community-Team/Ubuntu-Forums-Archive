---
title: "Broadcom Help!!"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by GameKing505 on 2007-11-03
Let me begin by saying I am a complete noob to Ubuntu, and Linux in general. I downloaded vista, didn't like it, and decided to ditch windows. 

Hearing good things about Ubuntu, I downloaded it and installed v7.10 (Gutsy Gibbon). It seems awesome, but the wireless does not work at all. I am posting this through my XP Partition, which has no problems with my wireless card.

I've tried a million tutorials, reinstalled Ubuntu multiple times. I must have installed around 15 drivers with ndiswrapper, and still nothing. I'm ready to kill myself, but I figure before I forget about Ubuntu, I will ask for help on these forums.

Keep in mind I know nothing about Linux, so speak to me as if I'm an idiot.

My computer is a Gateway MX6453
As far as I know, my wireless card is: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01).

PLEASE HELP ME! :confused:

I really don't want to go back to windows but If I can't use the internet on Ubuntu, I will have to.

PS. I do not have a wired connection to the internet, so any downloading in Ubuntu is impossible. I would have to download in XP, save to a flash drive, and then boot into Ubuntu and do whatever it is I have to.

---

### Post by kevdog on 2007-11-03
If you have tried a lot of tutorials, what part are you having trouble with?

---

### Post by GameKing505 on 2007-11-03
It's not a particular part I'm having problems with. I finish the tutorial, reboot, and it simply doesn't work. Maybe I'm not using the right drivers or something?

In one of my tries I actually used ndiswrapper to load the SAME EXACT driver that I use in my windows partition, but it still didn't work.

---

### Post by kevdog on 2007-11-03
Please postthe following

lshw -C network
modinfo ndiswrapper
ndiswrapper -l

---

### Post by GameKing505 on 2007-11-03
jimmy@jimmy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:e0:b8:b8:73:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


jimmy@jimmy-laptop:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.45
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     C23EAF5C384606A1A10E453
depends:        usbcore
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


jimmy@jimmy-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

---

### Post by kevdog on 2007-11-03
Can you do the following:

sudo modprobe ndiswrapper

Then post the following:
lshw -C network

---

### Post by GameKing505 on 2007-11-03
jimmy@jimmy-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for jimmy:
jimmy@jimmy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:e0:b8:b8:73:35
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:14:a5:ea:32:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by kevdog on 2007-11-03
All good for right now - your wireless device is eth0.

Make sure you do the following
echo ndiswrapper | sudo tee -a /etc/modules

This loads the ndiswrapper program at startup.  Try network manager now to connect to an unencrypted network or WEP network.  WPA requires additional steps.

---

### Post by GameKing505 on 2007-11-03
I really apologize for being such an idiot, but I still don't see any networks. When I click the icon of the two monitors which I'm pretty sure is the network manager, it only has a greyed out "wired connection" and an option to configure manually. It doesn't say anything about wireless stuff. Once again, I'm sorry for the trouble.

---

### Post by kevdog on 2007-11-03
sudo ifconfig eth0 up
iwlist scan

What does this show?

---

### Post by GameKing505 on 2007-11-03
I'm posting from Ubuntu now!

I realized that I did not set it up to start at the boot like you said, so I just repeated the command, and now it works!!!

Only one problem. Ubuntu can see my network, but I cannot access it because it is encrypted somehow through WEP or WPA or something. I have the key, but when I put it in it just stalls forever. Any help?

PS. I'm posting this through my neighbor's network, not my own.

---

### Post by GameKing505 on 2007-11-03
I made a stupid mistake and forgot to set it up at boot, but now I'm posting through Ubuntu!!!

Let me begin by thanking you. You have helped me to ditch the crap that is Windows and go with a free, better, and less bloated solution.

...Unfortunately, there is one small problem. My network is seen by the manager, but I cannot access it because it is encrypted through WEP or WPA or some junk like that. THe only way I can get on the net now is through my neighbors (really slow) network.

Any way to fix this?

PS. THANK YOU SOOOOOOOO MUCH!!!!

---

### Post by GameKing505 on 2007-11-03
Gah. The slow connection made me think my post didn't go through. Sorry for the double post. (I guess it's a triple now)

---

### Post by kevdog on 2007-11-03
Is it WEP or WPA -- it makes a difference??

---

### Post by GameKing505 on 2007-11-03
How do I tell? In windows it just says "security enabled wireless network"

EDIT: After some searching, I've found out that it's WEP.

---

### Post by kevdog on 2007-11-03
How are trying to connect -- if using network manager enable roaming mode.

---

### Post by GameKing505 on 2007-11-03
That did it. I'm fully connected at 54 mbs, and couldn't be happier. Thanks loads. I thought I'd never be able to ditch windows...

---

### Post by GameKing505 on 2007-11-03
Easy come easy go. It's gone again. I have no idea why...

All I did was reboot, but I did that commadn you told me. I was so happy...

---

### Post by GameKing505 on 2007-11-04
Please can anyone help? It just stopped working for no reason. All I did was install some stuff completely unrelated, and now it's gone.

Any help would be GREATLY appreciated.

---

### Post by GameKing505 on 2007-11-04
Bump?

---

### Post by foolios on 2007-11-07
Were you able to resolve this?

---

### Post by GameKing505 on 2007-11-08
In a way... 
For some reason when I boot up there is like a 50/50 shot of my connection working. When it doesn't, I've written myself a quick script that uninstalls ndiswrapper, then reinstalls it,and then installs the driver. Ths is just my quick fix though. I would still like to know what is going on...

---

