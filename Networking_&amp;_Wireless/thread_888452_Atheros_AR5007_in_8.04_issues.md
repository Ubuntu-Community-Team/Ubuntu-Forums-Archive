---
title: "Atheros AR5007 in 8.04 issues"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by cr0bar on 2008-08-13
So, I recently got back into Ubuntu and installed 8.04 not long ago. I obtained the 32-bit XP drivers for my wireless card and I believe I followed the instructions correctly, but I must be missing something.

sudo ndiswrapper -l yields the below:

netathr : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

However after depmod and modprobing ndiswrapper the card fails to show in the network config manager, and iwconfig says there are no wireless extensions present.

Have there been similar issues with this specific wireless card?

---

### Post by Crafty Kisses on 2008-08-13
Post the following outputs:
```
lshw -C network
```
Then the next one:
```
iwconfig
```

---

### Post by cr0bar on 2008-08-13
Cheers for the quick reply, lshw -C network is below:

>   *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:58:5c:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.91 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

iwconfig is below:

> lo        no wireless extensions.

eth0      no wireless extensions.



EDIT:

Problem solved.

---

### Post by nicedude on 2008-08-19
I have a step by step guide with aircrack patched driver for download here in the forums that if you are using 32bit Ubuntu Hardy is 100% working for the AR5007 and supports WEP & WPA as well as Monitor mode and injection ( for wifi hacking ). I would suggest that the Madwifi driver is superior to using Ndiswrapper and allows you to have more functions and great performance.

HERE IS MY AR5007 GUIDE
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

If anyone who uses it needs help just PM me and I will try to help.

nicedude

---

