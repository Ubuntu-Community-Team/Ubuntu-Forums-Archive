---
title: "Dell M1330 wireless problems"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by udrunk2? on 2008-05-23
I am having a very difficult time logging into my wifi network.  The trick is once I do I have a (nearly) flawless signal and can surf at speed. I am fairly new to ubuntu and have been experimenting.  The router runs into lots of interference (apt.) and is running WPA2.  I have tried unsecure, WPA, and WEP.  The other trick is that Vista has no problems locating the network neither does any other of the laptops.  
My guess is either ubuntu is not roaming or authenticating properly?????

Some more info:
 *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:59:6b:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.0.119 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:81:e2:c3
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair


Thank you all,
CW

---

### Post by mapes12 on 2008-05-23
Your post indicates that you have had some success with accessing your wifi connection. If this is the case you might want to consider installing an alternative to Network Manager:

These links provide further information:

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

:guitar:

---

### Post by udrunk2? on 2008-06-19
Tried and failed.  Wicd 1.4.2 detects SSID in the room, doesn't if there's any range.  Does not connect to WPA2 at all.  Worked unsecured for awhile but cannot go back to that here.  Awaiting magic.

---

