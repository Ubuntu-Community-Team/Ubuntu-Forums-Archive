---
title: "AR938x unclaimed"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by some14 on 2016-06-23
Hello all, I am having trouble getting a AR938x wifi card working with Lubuntu 16.04

Output from lshw -C network below: ```


  *-network UNCLAIMED     
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: [EMAIL="pci@0000:06:00.0"]pci@0000:06:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:80400000-8041ffff memory:80420000-8042ffff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: [EMAIL="pci@0000:08:08.0"]pci@0000:08:08.0[/EMAIL]
       logical name: enp8s8
       version: 10
       serial: 00:1b:38:34:64:bd
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
```

---

### Post by jeremy31 on 2016-06-23
Moved to Networking
Please use code tags when posting terminal output and see the wireless script link in my signature, post results

---

### Post by some14 on 2016-07-03
Thank you, but as a newb I seem to be unable to run the script, i have copied all text into a text file under windows notepad, and copied it onto the desktop of the machine in question, if i navigate to the desktop within terminal i get syntax errors trying to run it using bash

---

### Post by jeremy31 on 2016-07-03
Post the result of ```
ls Desktop | grep wireless
```

---

