---
title: "ndiswrapper-1.47"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by hoscha on 2007-07-04
I recently downloaded ndiswrapper-1.47 from the website everyone says too......By the way I am using my windows xp right now.....i put ndiswrapper-1.47 on my desktop and also extracted their too....i also put my wireless drivers on the desktop too....I am very new to Ubuntu and do not really know the commands for the terminal window....so how exactly do i install ndiswrapper? and what commands do i exactly use to get it installed and i do realize my "username" will be different than who ever answers this....one person said to me....."point your present workng directory to the desktop. (cd Desktop) the cd to the ndiswrapper directory"....to me that is confusing, but either way everything is on the desktop and extracted too...i just wanna get my ndiswrapper-1.47 installed and my wireless drivers....so plz if anyone can help me that would be great...thanks for you time..
alex

---

### Post by zipperback on 2007-07-04
> i put ndiswrapper-1.47 on my desktop and also extracted their too....i also put my wireless drivers on the desktop too....I am very new to Ubuntu and do not really know the commands for the terminal window....so how exactly do i install ndiswrapper? and what commands do i exactly use to get it installed and i do realize my "username" will be different than who ever answers this....one person said to me....."point your present workng directory to the desktop. (cd Desktop) the cd to the ndiswrapper directory"....to me that is confusing, but either way everything is on the desktop and extracted too...i just wanna get my ndiswrapper-1.47 installed and my wireless drivers....so plz if anyone can help me that would be great...thanks for you time..
alex



**What specific kind of hardware do you have?**
It might be that you don't need to use the ndiswrapper.

Search the ubuntuforums.org for "ndiswrapper"

Also the ndiswrapper website has a forum as well.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/)

- Jack:popcorn:

---

### Post by hoscha on 2007-07-04
> **zipperback said:**
> **What specific kind of hardware do you have?**
It might be that you don't need to use the ndiswrapper.

Search the ubuntuforums.org for "ndiswrapper"

Also the ndiswrapper website has a forum as well.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/)

- Jack:popcorn:

I have tried everything to the nature of you said this....i even downloaded ndiswrapper from the link you gave me...and i can not seem to get anything to work....all i want to to get my wireless card working...and in the device manager...it says the PCI wireless card is there...so how do i get it running...

---

### Post by S15_88 on 2007-07-04
what wireless card do u have?

---

### Post by hoscha on 2007-07-04
> **S15_88 said:**
> what wireless card do u have?

i use Linksys WMP54G the version i believe is 3.100.46.0...and i just installed this ubuntu and so far i have done these commands..of course with the live cd in the cdrom
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

---

### Post by hoscha on 2007-07-04
here is an update on what i have done,  here are the commands...and the crap it spit back out at me after i did the commands. also i did updates by hard wiring it and i am using ndiswrapper-1.9    i guess it got that through the update, but whatever. i got ndiswrapper to install i believe because i went to the Synaptic Package Manager and installed it that way...
sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.

then i went to line 174 to see what it says...
open(INF, $filename) or die "couldn't open $filename: $!";

then i tried this
sudo ndiswrappper -i ~/desktop/bcmwl5.inf
driver bcmwl5 is already installed

then i did...
sudo depmond -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper...

so far that is all i have done, i am little more happy once i saw wlan0...also if this helps, when i go to system>Administration>Network
there are 3 devices  1)something about a Modem   2) something about my hard wire connection "which i had to use to update" 3: something about a wireless connection "although that was there right after i got done installing Ubuntu"

my router requires a SSID and 128 bit encryption code and is 26 characters...which i do have "but is it the same for ubuntu, because i have the one windows uses" and what is the difference between hexadecimal and ascii...cuz my password is something like this  653DA32E15005FCF and so on...anymore help would be great...thx

---

### Post by kevdog on 2007-07-05
No to blow off your question (your password is in hexadecimal btw), but can you connect without any WEP encryption?  When getting ndiswrapper up and running its good to take a stepwise approach and debug/verify things during the installation.  WEP just adds another level of complexity,possible failures to the mix!

---

### Post by fredj on 2007-07-05
If you installed ndiswrapper through the synaptic package manager and you are using Ubuntu Feisty then
your version of ndiswrapper is probably a non working one.
Go to Applications -> Accessories -> Terminal to open a terminal window. Then type ndiswrapper -v and
post the message that appears in the terminal window.

To be sure that you have a working version of ndiswrapper you will need to make and install the source files
you have downloaded to your desktop. Lets see if you have the faulty version of ndiswrapper first.

---

### Post by kevdog on 2007-07-05
Sorry I just re-read your post.  To the best of my knowledge the WMP54GS uses a ra chipset, that I believe is best installed using the serialmonkey cvs drivers, not ndiswrapper.  To verify this please post
lspci
lshw -C network

I know you have done all this work to get ndiswrapper installed, but I dont think it is going to be needed.

---

### Post by hoscha on 2007-07-05
[QUOTE=kevdog;2965044]Sorry I just re-read your post.  To the best of my knowledge the WMP54GS uses a ra chipset, that I believe is best installed using the serialmonkey cvs drivers, not ndiswrapper.  To verify this please post
lspci
lshw -C network

Here are the commands....and it says that my wireless card is disabled....so maybe thats the reason...how do i "enable it"...another question also is that people talk about this activate or deactivate buttons in the network connections, i do not have those buttons, all i have is the properties button and i am going to system>administration>network.

alex@Compaq-Ubuntu:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge 
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03) 
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) 
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80) 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) 


alex@Compaq-Ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0 DISABLED    
       description: Wireless interface 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 9 
       bus info: pci@00:09.0 
       logical name: eth1 
       version: 03 
       serial: 00:0c:41:60:20:e5 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 multicast=yes wireless=IEEE 802.11b/g 
       resources: iomemory:ea000000-ea001fff irq:20 
  *-network:1 
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@00:12.0 
       logical name: eth0 
       version: 78 
       serial: 00:11:2f:61:7c:e5 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.1.102 latency=32 maxlatency=8 mingnt=3 multicast=yes 
       resources: ioport:e000-e0ff iomemory:ea005000-ea0050ff irq:19

---

### Post by kevdog on 2007-07-05
Yes type in those commands at the terminal prompt and post the output. You can cut and paste!

---

### Post by hoscha on 2007-07-05
> **fredj said:**
> If you installed ndiswrapper through the synaptic package manager and you are using Ubuntu Feisty then
your version of ndiswrapper is probably a non working one.
Go to Applications -> Accessories -> Terminal to open a terminal window. Then type ndiswrapper -v and
post the message that appears in the terminal window.

To be sure that you have a working version of ndiswrapper you will need to make and install the source files
you have downloaded to your desktop. Lets see if you have the faulty version of ndiswrapper first.

alex@Compaq-Ubuntu:~$ ndiswrapper -v 
utils Error: no version specified! 
driver version:        1.38 
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by hoscha on 2007-07-05
> **kevdog said:**
> Yes type in those commands at the terminal prompt and post the output. You can cut and paste!

Here are the commands....and it says that my wireless card is disabled....so maybe thats the reason...how do i "enable it"...another question also is that people talk about this activate or deactivate buttons in the network connections, i do not have those buttons, all i have is the properties button and i am going to system>administration>network.

alex@Compaq-Ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


alex@Compaq-Ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network:0 DISABLED
description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 9
bus info: pci@00:09.0
logical name: eth1
version: 03
serial: 00:0c:41:60:20:e5
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
resources: iomemory:ea000000-ea001fff irq:20
*-network:1
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@00:12.0
logical name: eth0
version: 78
serial: 00:11:2f:61:7c:e5
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.1.102 latency=32 maxlatency=8 mingnt=3 multicast=yes
resources: ioport:e000-e0ff iomemory:ea005000-ea0050ff irq:19

---

### Post by sj3fk3 on 2007-07-05
> **hoscha said:**
> [QUOTE=kevdog;2965044]Sorry I just re-read your post.  To the best of my knowledge the WMP54GS uses a ra chipset, that I believe is best installed using the serialmonkey cvs drivers, not ndiswrapper.  To verify this please post
lspci
lshw -C network
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller        product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=32 multicast=yes wireless=IEEE 802.11b/g 


The driver is already in compiled and in your kernel as a module. All you need is the right firmware. Google for ubuntu and fwcutter and you will find the solution.
Or just click [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by sj3fk3 on 2007-07-05
> **kevdog said:**
> Sorry I just re-read your post.  To the best of my knowledge the WMP54GS uses a ra chipset, that I believe is best installed using the serialmonkey cvs drivers, not ndiswrapper.  To verify this please post
lspci
lshw -C network

I know you have done all this work to get ndiswrapper installed, but I dont think it is going to be needed.

product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation

It's broadcom he doesn't need ndiswrapper nor serialmonkey's all he needs is the firmware for his wireless nic. I use exactly the same nic.

---

### Post by hoscha on 2007-07-05
> **sj3fk3 said:**
> product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation

It's broadcom he doesn't need ndiswrapper nor serialmonkey's all he needs is the firmware for his wireless nic. I use exactly the same nic.

ok, i got it..thank you for all your help, i guess it helped that you have the same NIC, that i do...ur help was much appreciated...:D, i have you 2 thumbs up man....ur help was very good and easy to understand...if something should ever arise in the future....i will be asking you....although when i arrived at this site  [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
followed the directions, and after roboot, i never got the wireless signal bars up by the clock....so if you know how to get that for me up there, that would be great, if not, thats ok..thanks for all your help:KS

---

### Post by Count Doofus on 2007-10-21
You'll get that error @ line 174 if the case of the filename is wrong !

bla@blabla:~$ sudo ndiswrapper -i _WG511v2.INF_
installing _wg511v2_ ...
couldn't open _WG511v2.INF_: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174. becaause its lookng for the file _wg511v2.INF _: 

try bla@blabla:~$ sudo ndiswrapper -i wg511v2.INF (or Inf OR INf whatever check the case when the file is listed with the dir command)

open the inf with gedit and check the case there might not be the same remember you can get downright sloppy in windows.

had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

