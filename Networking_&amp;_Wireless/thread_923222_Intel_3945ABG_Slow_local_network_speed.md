---
title: "Intel 3945ABG Slow local network speed"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Covn on 2008-09-18
So this the thing:

I run Hardy on a Lenovo 3000 n200, and everything works fine except one thing. My 3945abg gives good enough internet speed, both up and down, but when I try to access the shares on my other computers (cabled desktops) I get riddiculously slow speeds.. We're talking 150-400 Kbps. A rate which would make it a lot faster downloading stuff from the web. It pretty much makes me unable to stream video or audio from my desktop computer to my laptop.

I did some searching and it seems this is a problem with the 3945 driver thats included in Hardy. I found a blog detailing a fix to the problem:

[http://clearpixels.net/2008/07/3945abg-fix-for-ubuntu/](http://clearpixels.net/2008/07/3945abg-fix-for-ubuntu/)

I followed those instructions, and was able to download, and install the xp driver in ndiswrapper without any sort of problems. When i got wifi-radar installed, and rebooted it is unable to detect any wifi network whatsoever. I know for a fact there is 6-7 networks within the vincinity that i should beyond a doubt find if everything was working as intended.

Ndiswrapper reports the driver installed correctly, with corresponding hardware located, so I'm a bit lost here. Is there a problem with my card, the ubuntu driver, wifi-radar, ndiswrapper or what? I'm getting a bit tired of having to bring my usb stick to my desktop pc and manually copy crap over to my laptop, when all the pc's are part of the same network anyway.

In advance, thanks.

---

### Post by Covn on 2008-09-18
Had to revert the changes to Network-manager now to even get cabled net to work it seems.

---

### Post by Covn on 2008-09-18
No one got any experience with this?

---

### Post by Crafty Kisses on 2008-09-18
Post the results of these commands:
```
lshw -C network
```
Then the next one would be:
```
ndiswrapper -l
```

---

### Post by Covn on 2008-09-18
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:98:68:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:0e:5f:09
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair

```

Ndiswrapper is not installed, as the driver currently in use is the native one. Installing ndiswrapper effectively disables my wifi.

---

### Post by Covn on 2008-09-22
Any update on this?

---

