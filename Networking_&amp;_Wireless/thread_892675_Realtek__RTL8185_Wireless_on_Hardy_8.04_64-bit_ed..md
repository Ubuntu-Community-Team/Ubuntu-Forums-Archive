---
title: "Realtek  RTL8185 Wireless on Hardy 8.04 64-bit ed."
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by shurguywutt on 2008-08-17
I am having trouble getting my Realtek RTL8185 Wireless network card working on my Gateway MX6426 Notebook.  This is my college laptop and it is important for me to get my wireless connection working.  Has anyone had experience getting this card to work?  I am somewhat new to Ubuntu and I have no Windows partition on my laptop.  

Here are the specs of my laptop  

[http://http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml]("http://http://support.gateway.com/s/Mobile/Q106/Blade/1014029Rsp2.shtml")

and are the results for the lshw -C network command from terminal.

> brandon@brandon-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:b6:3a:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=10.0.9.73 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32


Thanks a lot and any help anyone can give me will be greatly appreciated.

---

### Post by Paradoxfox93 on 2008-08-29
well i havent had any luck with 64 bit but hardy runs like a peach on my gateway in 32bit but you have to manually compile ndiswrapper and get the ME/98 driver from [www.realtek.com](www.realtek.com).  These instructions worked well for me:
[http://ubuntuforums.org/showthread.php?t=571129](http://ubuntuforums.org/showthread.php?t=571129)

let me know if you come across a solution for 64bit I'd love to get it running.

---

### Post by Crafty Kisses on 2008-08-29
Post this output:
```
iwconfig
```

---

