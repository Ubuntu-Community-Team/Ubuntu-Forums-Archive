---
title: "WPA on Prism 2.5 Wavelan"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by scubacuda on 2006-10-22
How do I get my built in wireless card to recognize my WPA network?  Right now, it only sees WEP.  I'm using 6.06.1 Dapper Drake Alternative.

For what it's worth, below is an excerpt from my **lshw** report.

           *-network:0
                description: Wireless interface
                product: Prism 2.5 Wavelan chipset
                vendor: Intersil Corporation
                physical id: 4
                bus info: pci@02:04.0
                logical name: eth0
                version: 01
                serial: 00:20:e0:a8:a8:ae
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list ethernet physical wireless
                configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.6 ip=192.168.1.101 link=yes multicast=yes wireless=IEEE 802.11b
                resources: iomemory:f0018000-f0018fff irq:10

---

### Post by randomnumber on 2006-10-22
I would try wpasupplicant.

You may need to add details about your network so that others may be able to help. 

Some other thread that may be useful [http://ubuntuforums.org/showthread.php?t=249654](http://ubuntuforums.org/showthread.php?t=249654) .

good luck.

---

