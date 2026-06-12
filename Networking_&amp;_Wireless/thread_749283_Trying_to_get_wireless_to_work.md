---
title: "Trying to get wireless to work"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by DanseNoir on 2008-04-08
I'm a newbie and I cannot figure out how to get my wireless to work.  I've tried clicking on the icon in the upper right-hand corner and setting it up that way, but it never seems to work. When I use any of the three methods available, it appears as if Ubuntu can't detect my connection. 

I read the [How to:  Manual Network Configuration]("http://ubuntuforums.org/showthread.php?t=571188") post at the top of the forum and when I entered the first code ("lshw -C network"), I got the following output:

>   *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:cf:8b:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5e:42:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=xxxxxxxx

Why does it say "network DISABLED" at the very top?  

I tried to follow the tutorial for a WEP Connection and entered the following:

> sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 "essid"
sudo iwconfig eth1 key XXXXXXXXXX
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

The first two lines seemed to work, but when I entered the third line ("eth1 up"), I got the following message, "SIOCSIFFLAGS: No such file or directory"

Perhaps I'm such an amateur, that I can't even be helped, but hopefully that's not the case :)  Any help in walking me through this or directing me to a thread that would walk me through this would be very appreciated!

---

### Post by gsimon on 2008-04-08
Hi DanseNoir,

What Ubuntu version are you using?

---

### Post by DanseNoir on 2008-04-08
I'm using 7.1 (Gutsy Gibbon).

---

### Post by upthelum on 2008-04-08
I had some difficulty getting wireless working on my laptop which there are no Dell drivers for, but got it eventually. Post some specs to help people diagnose your problem. Post output of:
lspci
iwconfig

I may not be able to help much but this along with your machine spec should give a better idea what to do for you.

Try this [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

---

### Post by DanseNoir on 2008-04-09
OK, so I'm running the tutorial you linked to.  On Step #2 for Installing "Build Essential", I made it through direction #2, but as I'm completely a newbie here, I have no idea what to do when I get to direction #3 which says

> "3) Once [Build Essential] is downloaded, transfer the file to the computer you are trying to configure wireless on. Put it in its own directory (folder)."

How do I put it in its own directory and what do I need to type in terminal to get into that directory in order to complete direction #4?  I'm not sure if the output thus far is of any use, but just in case it is:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3940kB/7935kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main linux-libc-dev 2.6.22-14.52 [653kB]
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Fetched 3940kB in 1m26s (45.7kB/s)                                             
Selecting previously deselected package linux-libc-dev.
(Reading database ... 92671 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.52) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...


---

