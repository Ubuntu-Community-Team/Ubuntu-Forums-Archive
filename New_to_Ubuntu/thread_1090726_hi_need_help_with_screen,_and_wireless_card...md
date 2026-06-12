---
title: "hi need help with screen, and wireless card.."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mzunguu on 2009-03-08
hi please i would like to ask for help, i installed ubuntu 8.10 on Fujitsu siemens amilo pro v2055 and default screen resolution is 1600@..., and i need 1200@800. how do i do that, and more the OS doesnt recognize the monitor,then i cannot get driver for my wireless card...,
i was here in forum before,but i forget my password so i am asking again now. sorry for that. 
if you can help . i will check tommorow.
thanx. :)

---

### Post by anewguy on 2009-03-08
Let's start with just the basics:

In a terminal window (applications/accessories/terminal):

type

lspci

and press enter.  Copy/paste the output from that back in a reply here.

Do the same for the following:

lsusb


Both of these will return a little more information that what we will need, but it's best to have too much than too little and have to ask for more.

We'll see if we can help after you post the above back here.

Dave :)

---

### Post by benit on 2009-03-09
For the Screen resolution problem have a look at [http://ubuntuforums.org/showthread.php?t=1085719&highlight=amilo+v2055]("http://ubuntuforums.org/showthread.php?t=1085719&highlight=amilo+v2055")


let us know if this worked for you, Good luck!

---

### Post by mzunguu on 2009-03-09
that's exactly what i did, i rewrote xorg. as was in that article and it didnt work, screen after boot, was just black.....

so.., i am lost..,sort of right now.., but ubuntu is very nice system, i like it so why i am trying to allow it work on my machine

---

### Post by ivanvajar on 2009-03-09
> **anewguy said:**
> Let's start with just the basics:

In a terminal window (applications/accessories/terminal):

type

lspci

and press enter.  Copy/paste the output from that back in a reply here.

Do the same for the following:

lsusb


Both of these will return a little more information that what we will need, but it's best to have too much than too little and have to ask for more.

We'll see if we can help after you post the above back here.

Dave :)

Would you kindly do as The Man said :-)

---

### Post by mzunguu on 2009-03-09
alright , then here it is, what terminal says..

lsusb

you@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
you@ubuntu:~$ 


you@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
you@ubuntu:~$ 

that is all what it says.., if you have any idea's , i will be very happy, to get help with this. thanx.

---

### Post by anewguy on 2009-03-09
The only real choice you have for a video driver is to go openchrome and get their driver.  The S3 unichrome pro is the exact same thing I had on a laptop a few years ago, and driver support is spotty.  You need to start with the driver, then work in xorg.conf to make changes.  When you are ready to try to change xorg.conf, after installing the driver, post back.

Your wireless is the ubuiquitous Broadcom 4318.  There are MANY post on this forum for getting it working, using either the restricted b43 driver or using ndiswrapper and a windows driver. 

Try reading through this link:

[http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215]("http://ubuntuforums.org/showthread.php?t=507505&highlight=gateway+mx3215")

even though it's not for your computer, the wireless and video are the same.  If you decide to use ndiswrapper as mentioned in the thread (it was written back for 7.04) then you will also need to add the b43 module to the blacklist file.

After you read through that and some of the threads for getting both the unichrome pro and the BCM4318 working, if you still have
questions or problems please post back.

Dave :)

---

