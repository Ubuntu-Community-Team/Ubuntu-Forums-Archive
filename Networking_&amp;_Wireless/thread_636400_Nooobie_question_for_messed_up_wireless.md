---
title: "Nooobie question for messed up wireless"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Joe.Kent on 2007-12-09
I successfully installed 7.10, had the wireless working on belkin 54g wireless card, then I changed something, and now I have no wireless. Can anyone tell me where to start diagnosing?

---

### Post by carlos1992 on 2007-12-09
first what do you change there are no magicians here lol (at least i don't know)
and maybe your system specs

---

### Post by Joe.Kent on 2007-12-09
> **carlos1992 said:**
> first what do you change there are no magicians here lol (at least i don't know)
and maybe your system specs


That is the problem, I'm not really sure what I changed, it was detecting the network at the boot up, then on restart it didn't so I went to the network configurator under admin and now I have no wireless. I even tried disabling and enabling the restricted drivers... 

This is on a Dell latitude 600 with 1ghz pro, 256 ram, 20gb hdd..... and ubuntu 7.10 installed via alternate cd...

---

### Post by Joe.Kent on 2007-12-09
Digging into the network settings, I found that if I enable roaming, I can see the signals again, but I cannot connect, when I turn off roaming, I loose all wireless signals and it says wireless disabled, can anyone help?

---

### Post by kevdog on 2007-12-09
Can you post

lshw -C network

Other than telling us about your problem thoroughly, you havent given us any information that we can use to help you.

---

### Post by Joe.Kent on 2007-12-10
joe@Dell:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c556 Hurricane CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 00:04:76:3f:62:cd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=5 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:11:50:97:68:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


hope this helps...what more info do you need kev?

---

