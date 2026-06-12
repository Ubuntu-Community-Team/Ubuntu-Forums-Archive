---
title: "Need help with installation of 10.04.02 LTS"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by chill3d on 2011-07-18
I am trying to install 10.04.02 64 bit. The OS prior to linux was Vista 64 bit. I have installed Ubuntu in system with a clean install, deleting any other OS.
During installation I noticed that the laptops display had lines through it. like horizontal blinds if you will. I noticed this and thought I would complete the install, thinking I may just need a graphics driver. Once completely installed, the display was still with the blinds and then i noticed no wifi connectivity. The 2500 has a switch on the base of it for turning the wifi on and off. turned either way produces nothing. 
I have already installed Ubuntu 10.04.02 LTS on this Laptop a hp dv7 and it works perfectly. 
pLEASE HELP! Thanks

---

### Post by alphacrucis2 on 2011-07-19
> **chill3d said:**
> I am trying to install 10.04.02 64 bit. The OS prior to linux was Vista 64 bit. I have installed Ubuntu in system with a clean install, deleting any other OS.
During installation I noticed that the laptops display had lines through it. like horizontal blinds if you will. I noticed this and thought I would complete the install, thinking I may just need a graphics driver. Once completely installed, the display was still with the blinds and then i noticed no wifi connectivity. The 2500 has a switch on the base of it for turning the wifi on and off. turned either way produces nothing. 
I have already installed Ubuntu 10.04.02 LTS on this Laptop a hp dv7 and it works perfectly. 
pLEASE HELP! Thanks

Did you test the wireless from the live CD before installing?


You will probably need internet access to fix things up. Try connecting wired if possible and then System - Administration - Hardware drivers and install any available proprietary drivers. Then make sure you are fully up to date:

```
sudo apt-get update
sudo apt-get upgrade
```

If still no joy what do you get from:

```
sudo lshw -C network
```

---

### Post by chill3d on 2011-07-19
I have no access to a wired connection unfortunately.

this is what i get after sudo code

:

*-network               
       description: Ethernet interface 
       product: MCP67 Ethernet 
       vendor: nVidia Corporation 
       physical id: a 
       bus info: pci@0000:00:0a.0 
       logical name: eth0 
       version: a2 
       serial: 00:1d:72:54:e9:c4 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII 
       resources: irq:27 memory:fc488000-fc488fff ioport:30f8(size=8) memory:fc489c00-fc489cff memory:fc489800-fc48980f 
  *-network 
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:22 memory:fc000000-fc003fff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:21:00:11:47:e4 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Wim Sturkenboom on 2011-07-19
I guess you need to install the broadcom driver; I don't know how to do it without a network connection.

With regards to the video, when you get to the grub menu, press 'e' to edit the highlighted entry and add *nomodeset* at the end of the line with '*quiet splash*' so it looks like '*quiet splash nomodeset*'. Next press <ctrl>X to boot

If this solves the issue, that change can be made permanent. You might however have a low resolution.

PS
output of lspci can be useful to determine the videocard that you have; I guess a nvidia one (from the previous output that you posted).

---

### Post by alphacrucis2 on 2011-07-19
[http://ubuntuforums.org/showthread.php?t=1620585]("http://ubuntuforums.org/showthread.php?t=1620585")

The above may help with the broadcom issue. You will need internet access from another PC and transfer the driver via USB flash I guess.

---

### Post by wildmanne39 on 2011-07-19
Hi, here is a link that tells step by step how to setup your wireless card and down the page a ways it tells you how to get the driver and install it without a internet connection.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by mastablasta on 2011-07-19
ups wrong post...

---

