---
title: "Major networking problem"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by TheFoe92 on 2007-07-19
I don't even know how to start or explain my problem! I was trying to enable internet sharing so that I could transmit the wireless internet my laptop receives to my PC that is too far from the router through a crossover Ethernet cable. I used these sites : [http://ubuntuforums.org/showthread.php?t=76346]("http://ubuntuforums.org/showthread.php?t=76346") and [http://www.fs-security.com/docs/connection-sharing.php]("http://www.fs-security.com/docs/connection-sharing.php").
If it is hard to understand what I was trying to do, here is a diagram:

ROUTER ))))))) LAPTOP ------- PC

))))))) = wireless
------- = wired

I also wanted to be able to play a multiplayer game (StarCraft) with my PC through the direct Ethernet connection. I remember when I played this game on Windows, it was a lot easier: the PC didn't have to be connected to the internet; I just needed to connect my laptop with my crossover cable, configure it, and then play. Ubuntu must support this. But I don't know how to do it. After following the aforementioned websites, my wireless connection went completely dead! Network manager does not show any available wireless connections; it doesn't even have that option anymore! I could only connect using a wired connection. I can't even connect using an Ethernet cable. I have a Gateway 7330GZ laptop with a Broadcom wireless card. I use the ndiswrapper driver. Nothing wrong with this: it was working perfectly fine before I followed the instructions on those websites. I have absolutely no idea what I did. :confused: I was messing around with the IP address, subnet mask and default gateway of my Ethernet card, but I have no idea how that could effect my wireless connection. Any suggestions on how I could fix my problem and achieve my goal (the diagram)? Any suggestions are greatly appreciated. Thanks in advance!

P.S. If you're wondering, I'm using my laptop to write this up, but I'm using Windows. It was my last resort! Also, if I was not thorough enough, feel free to ask me to elaborate.

---

### Post by TheFoe92 on 2007-07-22
My wireless light does not even light up when Ubuntu loads. Anyone? Helllllllllooooooooo!

---

### Post by fredj on 2007-07-23
Open a terminal and type 'sudo lshw -class network' and post the output from that here.

---

### Post by TheFoe92 on 2007-07-23
Here is the output of the 'sudo lshw -class network' command.
 
```
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:12:a2:8c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:e00fc000-e00fdfff irq:18
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:db:ac:21
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,02/18/2005, 3.100.64.1 ip=206.116.181.245 latency=64 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e00f6000-e00f7fff irq:19

```
After using the 'sudo modprobe ndiswrapper' to activate my wireless (the light turned on) and the 'echo 'ndiswrapper' | sudo tee -a /etc/modules' (to activate it on restart) commands, I can now use my wireless internet. But, I need Firestarter to be able to use it. I am connected to the router, but without Firestarter running, I cannot browse the net. So, I can browse the net, but only with Firestarter. I can live with this, but I would like to fix this. Why does browsing the net depend on Firestarter? Also, about the internet sharing, any suggestions?

---

### Post by TheFoe92 on 2007-07-24
Anyone?

---

### Post by TheFoe92 on 2007-07-27
Is this a bug? Something that can't be done?

---

### Post by Hugolp on 2007-07-28
> **TheFoe92 said:**
> Is this a bug? Something that can't be done?

I am pretty sure is a bug. Firestarter is giving problems to a lot of people, starting for me. Simple port administration needs a clean up in Ubuntu, cause firestarter is giving problems all arround.

Hugo

---

### Post by TheFoe92 on 2007-07-29
So where can I report a bug like this?

---

### Post by TheFoe92 on 2007-08-01
Since no one is answering, I have done a little research myself. If anybody else has this problem try [this site]("http://ubuntuforums.org/showthread.php?t=76647"). I haven't tried it yet, so try please feel free to post as I am unsure if this will work once and for all.

---

