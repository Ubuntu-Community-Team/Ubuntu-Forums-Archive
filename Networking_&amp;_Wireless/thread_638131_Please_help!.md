---
title: "Please help!"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by EZ2NV on 2007-12-11
Alright, I have a recently purchased Sony Vaio, model VGN-NR120E.  It came preloaded with Vista.  Now, I've been a Windows user all my life, and was recently exposed to the awesomeness of Linux by a friend.  I didn't want to completely commit to a new OS yet, so I have Vista and Linux dual booted on my laptop.  

Everything went fine, but the only problem is Ubuntu isn't showing my wireless card as working.  I have the Atheros AR5006EG 802.11 b/g Wireless PCI Express Adapter.  From what I have read this is a fairly common problem.  However, I haven't been able to find a fix.  Please help me!

P.S.

I don't know if this helps at all, but whenever I type 'sudo lshw -C network' into Terminal, here is what it displays:

*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1a:b7:6c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.7.103 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

---

