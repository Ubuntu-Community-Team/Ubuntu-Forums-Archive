---
title: "[SOLVED] No broadcom driver in Restricted Drivers Manager"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Benchrest on 2007-12-04
HP 6646US with Broadcom 4328 wireless. Gutsy 7.10 

Graphics driver does appear in RDM.

No broadcom driver in Restricted Drivers Manager. I suspect it is because I had my wireless turned off when I installed Gutsy. But I can't be the first to have done this. In researching this I find the broadcom wireless is the one thing that works in Gutsy. Not for me.

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth7
       version: a2
       serial: 00:00:6c:4f:df:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

As you can see it shows unclaimed. I have tried downloading the driver manually but without the RDM I don't see how to install it. 

I have also reinstalled the RDM and redownloaded the restricted modules.  

sudo apt-get install linux-restricted-modules

Rich

---

### Post by rustybronco on 2007-12-04
> **Benchrest said:**
> HP 6646US with Broadcom 4328 wireless. Gutsy 7.10 

Graphics driver does appear in RDM.

No broadcom driver in Restricted Drivers Manager. I suspect it is because I had my wireless turned off when I installed Gutsy. But I can't be the first to have done this. In researching this I find the broadcom wireless is the one thing that works in Gutsy. Not for me.

   *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
        search for posts on the bcm4328, some broadcom chipsets work ootb but not this one.

---

### Post by Benchrest on 2007-12-04
Thankyou, I found the entry that bcm4328 is not supported by the Restricted drivers manager. I will close this thread and pursue ndiswrapper. I have found reference that that will work. No luck so far, but entries suggest may need a fresh install.

---

