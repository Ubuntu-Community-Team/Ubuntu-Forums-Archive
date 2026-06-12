---
title: "RT2870 in lubuntu problem with driver"
date: 2015-09-22
forum: Networking &amp; Wireless
---

### Post by orazio3 on 2015-09-22
Hi , i'm new in the forum also in ubuntu (i used it but never before have installed a driver).

The problem is, i bought a USB WIFI adapter (rt2870) from ebay. I see a lot of threads about  this adapter with 'step by step' but i can't do nothing.

Sorry if i posted here in the wrong subforum and thanks !

---

### Post by Bucky Ball on 2015-09-22
Welcome. Right forum area. :)

First off, can you get online with a cable? If so, do an update with the USB wireless dongle plugged in. If you don't get any notification, check 'Additional Drivers' (I think that is under 'System' in Lubuntu but don't quote me). If nothing happening, open a terminal and:

```
sudo lshw -C network
```

Post the output here between code tags (see last link in my signature).

---

### Post by orazio3 on 2015-09-22
orazio@orazio-OptiPlex-GX520:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:b0:84:fc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe8f0000-fe8fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 56:de:3d:e2:81:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.125 link=yes multicast=yes

---

### Post by Bucky Ball on 2015-09-22
You almost got the [code] tags, just had < instead of [. Have changed them for you.

Please run the command again with the wireless dongle plugged in and repost. :)

---

### Post by orazio3 on 2015-09-22
```

orazio@orazio-OptiPlex-GX520:~$ sudo lshw -C network
[sudo] password for orazio: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:b0:84:fc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5751-v3.44a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:fe8f0000-fe8fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 56:de:3d:e2:81:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.125 link=yes multicast=yes



```

---

### Post by Bucky Ball on 2015-09-22
Hmm. It was there the first time but I missed it as it is reporting the device as an ethernet interface, not a Network one. The RT2870 appears to not be easy to get working in Ubuntu, I'm sorry to say.

The best I found was ... try this:

[http://ubuntuforums.org/showthread.php?t=2210930&p=12955680&viewfull=1#post12955680](http://ubuntuforums.org/showthread.php?t=2210930&p=12955680&viewfull=1#post12955680)

chili555 is one of the wireless experts here and this worked for the user on the linked post for that card so fingers crossed. You will need to be online with a cable for this to work. It if works or doesn't, please post the results of the 'sudo lshw -C network' command again, please. :)

* Have you tried anything to get this going? You haven't dabbled with ndiswrapper? If not, good. Don't go there for now, or ever if possible. :)

*** Update: Scratch that. Go [here]("http://www.mediatek.com/en/downloads1/downloads/mt7612u/"), use a name and email (they can be ficticious) and download that driver. Extract it. In the DOP folder you will find a README file. In there, down that page a bit, it tells you how to install that driver. Give that go. It is for your card.

I have my fingers, and toes, crossed. :)

---

