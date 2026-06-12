---
title: "Trouble Enabling Wireless Card"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Davidkidson on 2007-01-18
Hi everyone.
Just got a Compaq Presario V2000 and can't seem to get the wife to work. Appears to be recognized and have a driver. I think it's disabled because Ubuntu doesn't recognize the wifi button on the laptop. How can I get the wifi button to work, or Enable the Device manually? Any help on this would be greatly appreciated!

lshw outputs:

*-network:1 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@05:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:7e:71:8c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:c0204000-c0205fff irq:225


Cheers,
David

---

### Post by spd106 on 2007-01-18
Try this wiki page [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)
It says bcm4311 but it applies to your bcm4318 as well. This can be tricky to get working, have a search for 4318 in the forum as well.

---

