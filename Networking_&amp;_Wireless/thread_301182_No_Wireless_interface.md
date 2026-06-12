---
title: "No Wireless interface"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Jonq on 2006-11-16
Hi,

I have installed Edgy this morning and since then I'm trying to get wireless working no luck so far, I cant see wireless interface in networking window, i have installed ndiswrapper and network manager but it just wont work I dont know what to do :-? and I'm about to lose my mind pls someone help ](*,)

---

### Post by huygens on 2006-11-16
Perhaps we could help if we knew which hardware you are using. Do you know the brand and product name of your wireless card?
For instance, I have a MSI card (PC54G3) based on the Ralink chipset RT61, and there is a [bug in Ubuntu 6.10 on Ralink RT61 driver]("https://launchpad.net/bugs/58117"). 
So we could perhaps help you better if you tell us more.

Huygens

---

### Post by Jonq on 2006-11-16
ofcourse sorry about that, Broadcom 4318 wireless card on Acer ferrari 4000

---

### Post by Jonq on 2006-11-16
btw if i do  sudo lshw -C network

i get
```

 *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:c0304000-c0305fff irq:11

```

---

### Post by Jonq on 2006-11-16
problem solved, removed everything (ndiswrapper etc) and rmeoved entry from blacklist reinstalled ndiswrapper rebooted and i have wlan in my network-settings now :D

---

### Post by backibaxter on 2006-11-28
What did you removed from the blacklist?
I'm already trying to set up my wifi for a few days now.
I have the ferrari 4000 and I've read a lot of forums. I hope you can tell me what to do to set up my wireless

---

