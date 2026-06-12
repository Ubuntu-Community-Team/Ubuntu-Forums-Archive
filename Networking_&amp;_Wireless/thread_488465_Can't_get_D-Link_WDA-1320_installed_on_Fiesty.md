---
title: "Can't get D-Link WDA-1320 installed on Fiesty"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by HimeNoHogosha on 2007-06-30
I am brand new to Linux, and am having a bit of trouble installing my wifi card (D-link WDA-1320). I bought this specific card because I had heard that it worked with ubuntu out of the box. I installed madwifi with no problems, however when I got to the step to do "modprobe ath_pci", I got no output. The result of me running lshw is :

lshw -C network  
network UNCLAIMED
description: Ethernet controller
product: AR5005G 802.11abg NIC
vendor: Atheros Communications, Inc.
physical id: 6
bus info: pci@04:06.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=168 maxlatency=28 mingnt=10
resources: iomemory:bebb0000-bebbffff irq:22

I don't really know what I'm doing so I tried following the newbie guides, searching forums, but I couldn't really find a solution. Please help :(

---

