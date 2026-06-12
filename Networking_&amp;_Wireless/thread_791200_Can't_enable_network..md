---
title: "Can't enable network."
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Waldemar Sikorski on 2008-05-12
Hi to all.
Total newbee I am. Total.
HP zv6233nr laptop.
I've installed ubuntu 8.04 as an app. I only have an iso no CD.
I'm on my 8th hour of frustration. Unfortunately I only have wireless connection at a cafe.
I can't make the network controller work. The wireless on/off button does not respond. 
I've installed wicd and it works - can't detect anything though.

What to do?

w@w-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bc:68:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:25:76:fd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
w@w-laptop:~$

---

### Post by dmizer on 2008-05-12
you'll need to look at this howto:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
you'll need to follow this step in the above howto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-3000cfb6eca52765e35274dce3d46285fdfdc0f4](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-3000cfb6eca52765e35274dce3d46285fdfdc0f4) 

you'll need ndiswrapper.  here's howto install ndiswrapper without internet:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?#head-6c3f75213ff90d97beac83ac70cd1a6574a16d27)

here's how to mount an iso image so it will function like a cdrom:
[https://help.ubuntu.com/community/MountIso?](https://help.ubuntu.com/community/MountIso?)

---

### Post by Waldemar Sikorski on 2008-05-13
Thanks dmizer but stil no go.
So far everything confuses me. 
I have so many conflicting informations as to what and how that it's hared to follow the right one. 
I download in windows onto a stick and load onto desktop in Hardy.
Many procedures are based on internet downloads to given locations with specific commands or from a cd.
As simple as it might be I still haven't installed ndiswrapper. So I think.

---

### Post by dmizer on 2008-05-14
you need ndiswrapper.  to install ndiswrapper, you will need to mount your ubuntu iso image.

perhaps this is a better howto (includes screenshots): [http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html)

once your iso image is mounted, then you will need to import the cd repositories, and then you will be able to install ndiswrapper.

once that's done, you can follow the howto i linked above.

---

### Post by mplexus on 2008-05-15
I might be wrong but the wireless button not responding might not have to do anything with ndiswrapper. I have successfully installed ndiswrapper but my wireless button does not respond as well - i refer to the button that enables/disables the wireless card (which could mean turning the cards power on/off ?).

Actually, it stops responding just seconds after i boot ubuntu ( [http://ubuntuforums.org/showthread.php?t=786473&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=786473&highlight=inprocomm) ) , so if i enable the card before booting into ubuntu everything works fine, and i have a wireless connection. But if i don't enable it before booting into ubuntu then i don't have the chance to enable it afterwards.

So, even if the ndiswrapper is installed, and recognizes the card, one must still be able to power their card on, through that external wireless button - which is dead. This is my problem anyway..

Just mentioned that if someone has any suggestions..

Btw, this problem occured only in Hardy. In Gutsy the button worked fine.

---

### Post by mplexus on 2008-05-16
Well i found my solution, if anyone by chance have similar problems with their acer aspire 1500 laptop series, I blacklisted acer-acpi module (/etc/modpobe.d/blacklist), and now my wireless button works fine. Probably my wireless button is a hardware one. Now I can connect/disconnect any time (with ndiswrapper of course and inprocomm 64bit drivers).

---

### Post by Waldemar Sikorski on 2008-05-17
Thanks again,

I've decided to take a shortcut and tether myself for now. 
I've downloaded as much as I could including gui enhancements.
I do have a question or three though: if not mistaken there is no equivelent of system restore. How to save the current setup (backup)?
I think there's a way of installing 8.04 in it's own partition without formating the drive and reinstalling windows-am I wrong?

---

### Post by dmizer on 2008-05-17
> **Waldemar Sikorski said:**
> I do have a question or three though: if not mistaken there is no equivelent of system restore. How to save the current setup (backup)?
I think there's a way of installing 8.04 in it's own partition without formating the drive and reinstalling windows-am I wrong?

here's how to backup your system with the command line:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) i've used it a number of times, and it works quite well but it does take some knowledge to make it function correctly.

i also went to system > administration > synaptic and performed a search on "backup" and found some potentially useful tools like backuppc and subversion, though i don't know much about either of these tools except that subversion is probably more than you're looking for.

this tutorial includes instructions on how to install without removing windows.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Waldemar Sikorski on 2008-05-17
dmizer,

Thank you as usual.
Well I'm untethered-finally.\\:D/
More questions.
I have a relatively old laptop zv6233nr (HP) with ATI RADEON XPRESS 200M IGP and 2GIGs of RAM. Everything seems to be working in compiz config (or so I think) except the cube. It will rotate horizontally but not vertically, on down arrow it unrolls into a film strip.
Is there anything that can be done about that?

---

