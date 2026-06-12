---
title: "Ubuntu search wireless networks too long and wireless led always is RED"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by vietnam on 2008-07-24
1. Ubuntu search wireless networks too long, I must use "connect to other wireless networks" to connect to known wireless network.

2. After that, when my computer connected, wireless is still RED (normal It must be BLUE when connected)

3. When I try turn off and re-turn on Wireless button, then wireless led will change to BLUE, but I can not connect to some wireless networks.

These is my pc:
1. Notebook Compaq V3307
2. Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

and here is lshw -C network
---------
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:52:15:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.254.2 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:94:dc:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
---------
Many thanks for your help!

---

