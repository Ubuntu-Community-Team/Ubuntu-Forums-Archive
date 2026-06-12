---
title: "Linksys Wireless-G Notebook Adapter WPC54G ver3.1 Help"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by rachely1k987 on 2008-08-11
I am pretty new to Ubuntu and am trying to get a new wireless adapter installed after my original was not compatible. I bought the Linksys WPC54G after reading that there was very little problems with installing but this is not my case! I have tried everything I can find on the forums to get it installed but none have worked.

With the sudo lshw -C network command I get

  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0

But I cannot find the wireless capability as with the iwconfig command I get

lo        no wireless extensions.

eth0      no wireless extensions.


If anyone has any ideas on what I con try please let me know!

---

