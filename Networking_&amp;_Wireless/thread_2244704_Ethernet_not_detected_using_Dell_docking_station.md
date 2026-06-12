---
title: "Ethernet not detected using Dell docking station"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by sakinyu on 2014-09-18
Hi everyone! I've seen that docking station isn't working really well with ubuntu... I tried with 12.04, and the beginning was okay. After some updates it stop working... BTW, I upgraded to 14.04, and it was working fine, a bit unstable ethernet connection, but good. Today, suddenly it doesn't work anymore... The only way to have wire connection is to use a gigabit USB adaptor... I don't know how to fix it, or how to detect the ethernet connection in the docking station. Maybe some drivers? The most weird thing is that it used to work at the beginning! :(

Some ideas??? S.O.S!!

When I'm connected with the gigabit USB-adaptor :

sudo lshw -c network
  *-network DISABLED      
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: 
       logical name: wlan0
       version: 
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:d0400000-d047ffff memory:bfa00000-bfa0ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth4
       serial: 
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=smsc75xx driverversion=22-Aug-2005 duplex=full firmware=smsc75xx USB 2.0 Gigabit Ethern ip=---.---.--- link=yes multicast=yes port=MII speed=1Gbit/s


and when I try to connect without the USB-adaptor:
*-network DISABLED      
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: -
       logical name: wlan0
       version: 01
       serial: -
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:d0400000-d047ffff memory:bfa00000-bfa0ffff

---

