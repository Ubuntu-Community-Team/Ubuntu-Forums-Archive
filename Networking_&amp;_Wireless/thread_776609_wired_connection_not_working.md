---
title: "wired connection not working"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by quickquest88 on 2008-04-30
after making some progress with my wireless card (brdcm 4318, now at least it shows up i the network tool) now my wired conection quit working.  It was working previously, that's how I gort as far as I have, now my wired connection no longer shows up in ifconfig,

anyone got any clues???

lshw -C network

*-network:0 UNCLAIMED
description: ehternet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id:0
bus info: pci@0000"02:00.0
version: 02
width: 32 bits
Clock: 33 mhz
capabilities: cap_list
configuration: latency=64

{had to type that all in by hand)

---

### Post by Ayuthia on 2008-04-30
Are you blacklisting b44?  That is your wired driver.  You will need to load that after ndiswrapper (if that is why you are blacklisting it).

---

