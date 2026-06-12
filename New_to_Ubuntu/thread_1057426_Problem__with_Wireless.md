---
title: "Problem  with Wireless"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Suuuuzy on 2009-02-01
The first time I tried to get on my wireless network I was able to but now when I try to get on the window comes up and I enter the password but the enter button on the wireless connect dialog box is grayed out.  Does anyone know how to fix this.

This is my first day with Ubuntu.

TIA

---

### Post by newbee70 on 2009-02-01
> **Suuuuzy said:**
> The first time I tried to get on my wireless network I was able to but now when I try to get on the window comes up and I enter the password but the enter button on the wireless connect dialog box is grayed out.  Does anyone know how to fix this.

This is my first day with Ubuntu.

TIA

Suuuuzy;

you might want to give a little discription of what system your running 8.04.02 or 8.10 and if your dual booting with windows.

and you might also include something like: 

from terminal:   sudo lshw -C network

and others will have a better chance to assist you.

---

### Post by anewguy on 2009-02-01
Better yet would be to go to applications/accessories/take screen snapshot and capture the whole screen to an image, then post it back here so we can see exactly where you are and what the problem looks like.

Dave :)

---

### Post by Suuuuzy on 2009-02-28
I am dual booting Ubuntu 8.10 with Vista. Here is the screenshot requested. I hope someone can still help me. My wireless is working in Vista and the driver seems to have installed correctly in Ubuntu.

TIA,
Suuuuzy

---

### Post by Suuuuzy on 2009-02-28
... And here's the info from Terminal:

*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: xxx
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: xxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: xxx
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

edit: This is all greek to me, I'm a total newbie on Linux.

---

