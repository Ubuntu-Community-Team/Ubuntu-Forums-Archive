---
title: "Intel 394ABG disabled after update"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by brandoncolorado on 2008-10-19
Hello,

I installed Ubuntu 8.10 using the Windows installation method.  After restarting, Ubuntu loaded fine (I chose this computer after doing research to make sure it works with Ubuntu).  The wireless driver loaded correctly and I was able to connect to my network.  I was then prompted to do an partial update, and the computer downloaded about 200 mb of more things.  After restart, my Intel 394ABG is not loaded.  The light on the front of the laptop that is usually illuminated blue when the wireless switch is on will not turn blue now.

#1)  From what I can tell, this card is supposed to work correctly
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

#2)  When I look at the restricted driver box, nothing is there

#3)  I tried searching the forums, but '394ABG' only returns 3 results for me.

#4)  Here is the information from lshw

 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5b:a0:9d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:5c:e2:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:13:fb:78:c2:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A

---

### Post by darco on 2008-10-19
Well remember this is Ibex which is a Beta...anyways, that too happened to me. I connected my laptop via an ethernet cable then did a "partial" upgrade which downloaded the linux-firmware which solved the problem for me....You may want to check this link and also the Ibex forum

[http://ubuntuforums.org/showthread.php?t=949341&highlight=wireless](http://ubuntuforums.org/showthread.php?t=949341&highlight=wireless)

good luck
darco

---

### Post by brandoncolorado on 2008-10-19
> **darco said:**
> Well remember this is Ibex which is a Beta...anyways, that too happened to me. I connected my laptop via an ethernet cable then did a "partial" upgrade which downloaded the linux-firmware which solved the problem for me....You may want to check this link and also the Ibex forum

[http://ubuntuforums.org/showthread.php?t=949341&highlight=wireless](http://ubuntuforums.org/showthread.php?t=949341&highlight=wireless)

good luck
darco

Thanks for that link, it points me in the right direction.  I was searching for the wrong card number! (missed the 5)  Also, the reason I installed beta is because I booted using the liveCD to test everything at first.  During this test, everything worked wonderfully, so I assumed wireless wouldn't break.

---

