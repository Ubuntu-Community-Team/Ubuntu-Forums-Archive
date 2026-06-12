---
title: "NETGEAR WG511 v2  card help"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by V2JTB on 2009-04-07
Hi All,

I have an old Thinkpad T30 and bought a NETGEAR WG511 v2 made in China WIFI card.  I removed the original built in mini card so  I could use the PCMCIA card as I did not want any problems.  I am using the the Ubuntu 8.10 CD.

I have never used linux before and would like to make it easy and use a Wifi card that is supported out the box.  Could you give me some advice on what card to buy and how to get it working?

Almost a Ubuntu Linux user I have the Ubuntu software running from CD.

I got this working - lshw -C network - I used an i instead of l.  

ubuntu@ubuntu:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:13:bf:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: xxxxxxxxxxx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by iBurger on 2009-04-09
Perhaps repost this question here;

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332) 

Please make clear in the topic that you are looking for a compatible PCMIA wireless network card.

---

