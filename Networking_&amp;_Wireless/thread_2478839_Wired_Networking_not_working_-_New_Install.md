---
title: "Wired Networking not working - New Install"
date: 2022-09-06
forum: Networking &amp; Wireless
---

### Post by securitydad on 2022-09-06
I installed 22.04.1 LTS (Jammy Jellyfish)

ifconfig shows the following:

ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1211  bytes 119054 (119.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1211  bytes 119054 (119.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.216  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a6be:2a41:c62c:3167  prefixlen 64  scopeid 0x20<link>
        ether 7c:5c:f8:cb:c2:17  txqueuelen 1000  (Ethernet)
        RX packets 83133  bytes 18219068 (18.2 MB)
        RX errors 0  dropped 10  overruns 0  frame 0
        TX packets 16520  bytes 3065365 (3.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


shw -C network
  *-network DISABLED        
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:54:56:0d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.049.02-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:37 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: bb
       serial: 7c:5c:f8:cb:c2:17
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-47-generic firmware=17.3216344376.0 7260-17.ucode ip=192.168.1.216 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:40 memory:fe900000-fe901fff

I do not know why the network is disabled, or why the Network card cannot get the DHCP Address (this workied in 20.02).

Any clues?

---

### Post by securitydad on 2022-09-06
ifconfig enp1s0 up

Brings the interface up, but does not permit it to grab a DHCP address.

---

