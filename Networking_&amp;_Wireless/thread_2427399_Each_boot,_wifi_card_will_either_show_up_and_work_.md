---
title: "Each boot, wifi card will either show up and work perfectly, or not show up at all"
date: 2019-09-21
forum: Networking &amp; Wireless
---

### Post by skyturnred2 on 2019-09-21
It seems to be about 50/50 right now. I dual boot with Windows due to being in a dual degree program that requires both Linux and Windows. Sometimes I'll switch between them multiple times a day. 

If I boot up and it's there, then I don't have to worry about it at all. It will work flawlessly until the next boot at least.

If I boot up and it's not there, I just restart and it may or may not be there next time. 

I'm using a built-in wifi card on my motherboard. It is an [COLOR=#4D4D4D][FONT=&amp]AC 9560. I had a Mint install before and it always worked with every boot. But I wanted to switch to Ubuntu due to other problems I was having that Ubuntu solved. 

I also use a Kali Live USB to try and learn more about security and the card works every time. 

Based on my research, it should be supported natively. 

_____

Based on some stuff I found around googling, this is the output when running ```
lshw -C network
```

Output is below. I couldn't find anything wrong but I'm very, very noobish about network cards and drivers, etc. 

[/FONT][/COLOR]```
  *-network:0               
       description: Wireless interface
       product: Wireless-AC 9560 [Jefferson Peak]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 10
       serial: **********
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-29-generic firmware=43.95eb4e97.0 ip=********* latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:51934000-51937fff

```

I've obviously also updated and upgraded. This is a fresh install of Ubuntu 19.04 from 2 days ago.

---

