---
title: "LAN connection"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Creasey on 2008-12-09
Just dual booted my laptop Vista Ubuntu 8.04. no problems.  I have a wireless and lan conncetion on the laptop.  Turned off the wireless connection during installation.  Ubuntu hasn't found the LAN adapter, a Marvell Yukon.  Can't get to the repositories to set up the wireless connection.  No internet access at all.  Any suggestions?
Creasey

---

### Post by northern lights on 2008-12-09
Can you please post the output of ```
sudo lshw -C network
``` Thank you.

---

### Post by Creasey on 2008-12-09
*-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
I hope that this makes sense. Thanks
C

---

