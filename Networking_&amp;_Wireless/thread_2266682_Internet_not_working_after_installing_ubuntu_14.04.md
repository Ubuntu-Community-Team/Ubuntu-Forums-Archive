---
title: "Internet not working after installing ubuntu 14.04.2 (32bit)"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by carlosjesus593 on 2015-02-24
S[SIZE=2][FONT=arial]o here's the story, I installed ubuntu on an old compaq laptop that was running a 64bit windows XP,... While it was installing it gave me a choice to install ubuntu along side windows or to get rid of windows all together, since I didn't need windows I chose to get rid of it all together but here is where the problem starts,... while installing, my wifi light turned off (it's on the button that turns on and off the wifi) after that it went on with the installation and asked if i wanted the 3rd party software, I checked the box and later during the installation process the thing would get stuck on "Configuring bcmwl-**kernel**-source (**i386**)",... so later  I found out it was getting stuck there because I checked the "Install 3rd party software" box,... so I re-installed (without the 3rd party software box) and boom, I got ubuntu but no internet and when I press the little wifi button to turn it on again it'll stays off,... I tried with a wired connection but it didn't work ether. [/FONT]

[FONT=arial]So my adventure starts here,... (remember I know nothing about ubuntu at this point,... and still don't know much) [/FONT]
[FONT=arial]I start asking google and after a few clicks I find that I need to install "firmware-b43-istaller",... so I look it up and try)but I needed b43-fwcutter,... after sometime I end up installing a few things:[/FONT]
[FONT=arial]              broadcom-wl4.150.10.5.tar.bz2[/FONT]
[FONT=arial]              patch_2.6-2ubuntu1_i386.deb (that was already intalled)[/FONT]
[FONT=arial]so I got those two and the b43-fwcutter, and I thought I would be able to install the firmware-b43-installer and have wonder full internet again but NO,... after a lot more time I figure out I had installed a b43-fwcutter_015 for a firmware-b43-installer_018-2,... so I then got the b43-fwcutter_018-2_i386.deb and I was able to install the firmware-b43-installer. [/FONT]

[FONT=arial]AND GUESS WHAT?? ,... still no internet :c ,... I don't have a way to have a wired connection (not that it works on it ether way) so all this downloading and installing of "stuff"  was done with a USB and another laptop I have that does have a working internet connection. [/FONT]

[FONT=arial]So here I am a total noob with a will to fight for internet on his laptop (that I will try to use for science purposes,... on a program called IRAF that only works on UNIX),... 

PLEASE PLEASE HELP ME.[/FONT][/SIZE]

---

### Post by slickymaster on 2015-02-24
Hi carlosjesus593, welcome to the forums.

I'm moving your thread to the **Networking & Wireless** sub-forum, which is the proper venue for it.

---

### Post by carlosjesus593 on 2015-02-24
Many thanks. :KS

---

### Post by jeremy31 on 2015-02-24
Can you give us the info from ```
lshw -c net
``` and we will try to get you online as fast as we can

---

### Post by westie457 on 2015-02-24
Hi carlosjesus593.
If you boot your system using the installation media in 'Try' mode are you able to connect to the internet using a cable?
If you can it should be relatively easy to diagnose and fix your issue.
If you cannot connect in 'Try' mode we will have to do this the slightly harder way.

---

### Post by carlosjesus593 on 2015-03-01
> **jeremy31 said:**
> Can you give us the info from ```
lshw -c net
``` and we will try to get you online as fast as we can

Sorry for taking so long, I haven´t been able to get online,... but here it is 

lic@lic-Presario-V2000-EH463UA-ABA:~$ sudo lshw -c net
[sudo] password for lic: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:e2:b2:be
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.17 
       latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff

And there's news, I reinstalled the whole thing from zero, and now the wired conection works fine tho the 
wireless is still not working. Before I reinstalled I tryed the with the wired conection on the "TRY" option 
and it didn't work.

---

### Post by jeremy31 on 2015-03-01
```
sudo apt-get install firmware-b43-installer
``` should get it working after a reboot

---

### Post by carlosjesus593 on 2015-03-02
> **jeremy31 said:**
> ```
sudo apt-get install firmware-b43-installer
``` should get it working after a reboot


Yes, yes it did get it working :D Thank you so much. 
 
  What was wrong with it?? 
:s just curious.

---

### Post by margazhang on 2015-12-08
I can simply solve the problem by doing the following:

sudo gedit /etc/NetworkManager/NetworkManager.conf

Then I just change "false" in the file to "true" and then save and reboot. The problem is gone!

---

