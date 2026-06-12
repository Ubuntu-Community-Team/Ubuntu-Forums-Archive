---
title: "Weird kernel/wireless issue in Hardy"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by workingwriter on 2008-05-10
Hi folks!

I recently upgraded my Dell E1505 laptop from Gutsy to Hardy, and I have a bizarre issue with the associated kernel upgrade. Grub displays three Ubuntu 8.04 kernels I can boot to: 2.6.24-14 generic boots works beautifully and connects nicely with my 2WIRE DSL router. 

Both 2.6.24-16 and 2.6.24-17 (both generic) not only won't connect to the router, they cut the power to the router (red lights shine from Power and Broadband whenever I try to connect)!

FWIW, I successfully logged into another wireless network with the -16 kernel earlier this week.

Additional hardware information:
sudo lshw -C network

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:7f:fc:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=172.16.1.34 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:85:04:df
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s


I had no problems upgrading this machine to Gutsy.

What in heck is going on? What can I do about it? All thoughts appreciated.

---

