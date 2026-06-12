---
title: "Wireless need help to get it back!"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by jcm1107 on 2009-04-11
Hi my wireless internet worked when I first installed Ubuntu, but my screen resolution was low so I had to install an Nvidia driver, to install this driver I had to have all conflicting drivers removed. Well when I removed the drivers to install the new one for the graphics I must have removed my wireless. Could some one please help me, I just need to know what Ubuntu 8.04 would have used as default. My wireless card is PCI and it is Linksys. Thanks!

---

### Post by Didius Falco on 2009-04-11
Try this:

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

Good luck!!

---

### Post by superprash2003 on 2009-04-11
also post output of **lshw -C network** from the terminal

---

### Post by jcm1107 on 2009-04-11
> **superprash2003 said:**
> also post output of **lshw -C network** from the terminal

justin@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1d:92:ed:ec:75
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
justin@ubuntu:~$ 

Here is the results

---

### Post by superprash2003 on 2009-04-13
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

