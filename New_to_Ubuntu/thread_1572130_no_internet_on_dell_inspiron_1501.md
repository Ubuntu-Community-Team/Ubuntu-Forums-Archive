---
title: "no internet on dell inspiron 1501"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-09-10
just installed ubuntu netbook edition 10.04 on my daughters dell insiron 1501 and set up the wireless connection for my router, but on the wireless icon it states connection not ready and ive no internet.
any help appreciated , at moment im on my other laptop

---

### Post by marshmallow1304 on 2010-09-10
First try connecting to a wired connection and running System->Administration->Hardware Drivers.  If a driver is found, install it and reboot.  If not, open Applications->Accessories->Terminal, run
```
sudo lshw -c network
```
and post the output so we can see what wireless chip you have.

---

### Post by khelben1979 on 2010-09-10
Since this is a network related problem, it would be interesting to know something about the network chip which is inside, and to show us this information, type ```
lspci
``` from an X terminal and paste the information into this thread for analysis.

Also, I think that this blog: [Ubuntu on the Dell Inspiron 1501]("http://www.ubuntu1501.com/") would be worth some of your time and attention, if you feel really persistent in getting everything working over there. Some of the information isn't really up to date with the latest version of Ubuntu, but I think the basics is enough to get you started how it looks like.

---

### Post by m3t3ors on 2010-09-10
right got ethernet and installed broadcom drivers but still no wireless internet
heres the terminal report

john@john-laptop:~$ sudo lshw -c network 
[sudo] password for john: 
  *-network DISABLED      
       description: Wireless interface 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:19:7d:58:9e:d5 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:18 memory:d0200000-d0203fff 
  *-network DISABLED 
       description: Ethernet interface 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:19:b9:4e:fa:b6 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair 
       resources: irq:21 memory:d0300000-d0301fff 
john@john-laptop:~$

---

### Post by marshmallow1304 on 2010-09-10
Hmm... Any chance that your wireless is turned off?  For example, on my laptop, Fn+F11 toggles the wireless chip on and off.  My 'lshw -c network' never reports the wireless as 'DISABLED' when it's on, even when not connected to anything.

From page 19 of the Inspiron 1501 [Owner's Manual]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBMQFjAA&url=http%3A%2F%2Fsupport.dell.com%2Fsupport%2Fedocs%2Fsystems%2Fins1501%2Fen%2Fom_en%2Fpdf%2FHN926A00.pdf&rct=j&q=dell%20inspiron%201501%20manual&ei=ZbWKTMTSAYPvnQeq8ejzCg&usg=AFQjCNFadgjq0ZdrVTZKBYlONbmkcF09rg&sig2=zZRRr-uAxsf7bfm6d5R5oA&cad=rja"), it looks like there should be a light indicating when wireless is activated.  Try using Fn+F2 and see if anything changes.

---

### Post by spjackson on 2010-09-10
> **m3t3ors said:**
> right got ethernet and installed broadcom drivers but still no wireless internet

I have an Inspiron 1501 with what appears to be the same wireless card, and it works just fine for me on Lucid with the Broadcom drivers. I didn't have to do anything out of the ordinary. However, from reading other posts, it appears not everyone has had the same experience.

---

### Post by m3t3ors on 2010-09-11
on the latoptop its fn +f2 to turn wireless on, now i know it works as does the wireless card because untill last night it had windows 7 installed and all was fine.

---

