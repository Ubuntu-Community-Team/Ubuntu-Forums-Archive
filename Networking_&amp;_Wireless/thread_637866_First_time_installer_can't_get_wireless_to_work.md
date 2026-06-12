---
title: "First time installer can't get wireless to work"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by sparetalk on 2007-12-11
Hi, I'm not sure if this has been asked and answered (didn't find it in the forum) but the welcome message did say "don't be afraid to ask a question" :)
This is my first time with Ubuntu. My past experience is with unix and that too before there was any of this fancy GUI stuff.
I am trying to get my Toshiba Satellite M115 S3094 to run on Ubuntu. I've downloaded the .iso (7.10) and booted from the CD. I can't get the wireless (Intel 3945 ABG)  to work. It runs fine on XP in the same machine.
I gave the right WEP key and I still can't get it to work. I haven't installed 7.10 on the machine, I tried to configure networking from the CD to see if it works and it didn't, although the card did show as supported. It sees my home network.:confused:
How should I start to troubleshooting?

Thanks.

---

### Post by kevdog on 2007-12-11
Im glad you are comfortable with the command line.  It will make it so much easier.

Please post

lshw -C network

Also see my post about connecting at the command line -- Its a good reference with a lot of links at the bottom

Also here is my wireless primer:

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by sparetalk on 2007-12-13
Here's the output of the lshw command.
I followed your wireless primer and tried to get it working using the instructions given there. All I can say is that it did not work and I don't know why coz I honestly did not know what the commands did.
 
> ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:00:d1:5b:49:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.65 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:00:cd:ff
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

---

### Post by sparetalk on 2007-12-16
Is if failing because of the "wireless=unassociated" part? What can I do to fix it?

---

### Post by Edho on 2007-12-16
Yess..think so..

Same card for me..says...(on the end) 

configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.2 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g

---

### Post by Edho on 2007-12-16
I think the error is on the routerside.

---

### Post by sparetalk on 2007-12-16
It could be the router. I'm more inclined towards my new Ubuntu install (liveCD) as that same machine works on win xp while my office laptop connects to the same router without a hitch.
Any clues on what I could change to get the association right? One clue might be that wireless was IEEE 802.11g for a while and then disappeared.

---

### Post by Edho on 2007-12-17
Give more info.

Menu ....System...Administration...Network.
password
What do you see?

Select Wireless and hit "properties"
What do you see?

---

