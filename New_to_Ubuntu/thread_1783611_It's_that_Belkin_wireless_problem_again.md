---
title: "It's that Belkin wireless problem again"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Thomas2e on 2011-06-16
I have acquired an older model Think Pad, and decided that now was the time to try Linux. I have been wanting to try it for some time. When it was a windows XP machine, I connected with my wireless router with a Belkin wireless adapter F5D7010. My first foray into the Linux world was running Puppy Linux on a USB flash drive. The Belkin adapter worked fine. Since the Installation of Ubuntu 11.04 (Natty?) and the removal of WinXP I cant get it to work. I followed the steps in the help guide, with no luck, and browsing the forums i found no info on 11.04 (does thedistro matter a lot?).

Here is the info:

Adapter: Belkin wireless notebook Network Card IEEE 802.11g       F5D7010  a sticker on it says ver.1315

WHEN I ran the command:  [COLOR=#000000][FONT=DejaVu Sans][COLOR=#3C3C3C][FONT=monospace]"sudo lshw -C network" , I got the following:
[SIZE=1]*-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:7a:d1:cc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.4 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:d0200000-d0200fff ioport:8000(size=64)
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:d8000000-d8001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:0c:b9:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


This is a lot of stuff, I know, but I don't know exactly what is needed to help figure this out! any help would be appreciated.[/SIZE]
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-06-16
Hi, I had that same one and it had a driver that could be instaled. Look in addtitional drivers, you need to have a wired connection to the internet, then click on additional drivers and there should be one in there for you to activate, then reboot and go to network icon in the top right corner click on wireless and put in your password.

---

### Post by amanchesterman on 2011-06-16
Hi Thomas2e, I faced the same issue with an old XP laptop and a Belkin wireless card. As wildmanne39 says, the solution is to download a driver for the card -- and to do that you have to have a wired connection to your router. I just wanted to add, though, that I had to start up the laptop first and then connect the ethernet cable: if I started with the cable connected, the laptop didn't seem to realise that it was missing a driver for the wireless card.

---

### Post by psucrash on 2011-07-12
I'm running 11.04 (iirc) and the F5d7010v2 card I have was plug and play. When I run [COLOR=#000000][FONT=DejaVu Sans][COLOR=#3C3C3C][FONT=monospace]sudo lshw -C network it also shows the correct information. I do have an issue with random disconnections but I think that's a different issue. 
What version of the card are you using?
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by kgundry on 2011-07-14
I have a different but probably related problem.  My home computer is running Ubuntu 10.04.  The Belkin USB wireless device (actually a MyEssentials device, but it's the same thing) works provided I turn off security on my wireless network so no password is required.  When the security is activated, the Ubuntu computer rightly demands a password, but when I enter it, the symbol in the bottom right of the screen sometimes indicates connection (not always) but I don't actually have connection.  

I am typing this at work on a different Ubuntu computer (10.10), and again the device works without any effort on my part, but the only wireless network available lacks security and therefore does not need a password, so that doesn't prove anything.  Any ideas?

kgundry

---

### Post by gandaran on 2011-07-14
> **kgundry said:**
> I have a different but probably related problem.  My home computer is running Ubuntu 10.04.  The Belkin USB wireless device (actually a MyEssentials device, but it's the same thing) works provided I turn off security on my wireless network so no password is required.  When the security is activated, the Ubuntu computer rightly demands a password, but when I enter it, the symbol in the bottom right of the screen sometimes indicates connection (not always) but I don't actually have connection.  

I am typing this at work on a different Ubuntu computer (10.10), and again the device works without any effort on my part, but the only wireless network available lacks security and therefore does not need a password, so that doesn't prove anything.  Any ideas?

kgundry
maybe missing firmware! if its broadcom divers you are using check this guide to find exactly what you have to install
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

