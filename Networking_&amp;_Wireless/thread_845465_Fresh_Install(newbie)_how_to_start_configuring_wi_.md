---
title: "Fresh Install(newbie) :how to start configuring wi fi"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by levis lover on 2008-06-30
i have just installed ubuntu 8.04 LTS but now  want to connect my laptops wi-fi to the modem..
from where should i start?

lshw -C Network

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:03:25:45:2f:06
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:08:09.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32

---

### Post by chili555 on 2008-06-30
You might check here: [http://ubuntuforums.org/showthread.php?t=772006&highlight=RTL-8185](http://ubuntuforums.org/showthread.php?t=772006&highlight=RTL-8185) or here: [http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy)

---

