---
title: "problems with intel 3945"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by tropehjelm on 2008-08-21
Hi

I have some trouble getting my wireless network up and running:neutral:

Output from lshw -C network

  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:11:dd:6e
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x ip=10.4.153.1 latency=0 module=et131x multicast=yes

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945 

Is the driver installed correctly?

I tried searching the internet, but all the HOW-TO's assume that your wirlesscard has a logical name, mine dosen't :(   
(i'm new to linux so forgive me if im worng)

Maybe I forgot to turn on my wireless before I installed ubuntu, could this be the problem??

Søren

---

### Post by amedac on 2008-08-21
Please type ```
ifconfig -a
``` and give output here

---

