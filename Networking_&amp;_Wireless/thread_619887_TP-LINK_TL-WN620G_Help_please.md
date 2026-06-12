---
title: "TP-LINK TL-WN620G Help please"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by dynamethod on 2007-11-21
[B][U]***IVE TRIED INSTALLING THIS TIP-LINK TL-WN620G, READ THE REST BUT NOW THE OS IS COMPLETELY *&%^* IT SAYS KERNEL PANNICK EVERYTIME I BOOT, INCLUDING IN RECOVERY MODE, DO I HAVE TO REINSTALL COMPLETELY? I NOW RISK LOSING EVERYTHING!!!***

[/U][/B]
hey there im following this guide here: [https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper))

but at this part here:

   1.

      Use the WinXP drivers in the directory  TL-WN620G/Win2000_XP/Driver Files  of the installation CD:

r5523.bin  athfmwdl.inf  athfmwdl.sys  tl-wn620g.inf  tl-wn620g.sys  

   1.

      Install athfmwdl first, then tl-wn620g second:

$ sudo ndiswrapper -i athfmwdl.inf 
$ sudo ndiswrapper -i tl-wn620g.inf 

im completely stuck here, this is what i got after "sudo ndiswrapper -i athfmwdl.inf"   : couldn't open athfmwdl.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.


help much appreciated,

---

### Post by dynamethod on 2007-11-21
ok this is weird, because ive checked and /usr/sbin/ndiswrapper-1.9 does exist, what am i doing wrong?

---

### Post by dynamethod on 2007-11-21
ok solved the ndiswrapper problem following this guide : [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

however the "network" tool is not recognising my wlan

i tried lshw - C network 

but get: 

 *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:17:31:51:c5:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.243 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes

:S

---

### Post by dynamethod on 2007-11-22
im going to log into the IRC Ubuntu chat room, my Nick is "newguy" please help if you can cause my whole OS is now buggered...

---

### Post by dynamethod on 2007-11-22
well ive just reinstalled, ok ive got so far now, heres a screenshot of my situation now

one thing though i have 4 USB ports, so is there something i should be doing to help gutsy realise its a specific USB port or anything?

please help, im soo desperate, thanks

---

