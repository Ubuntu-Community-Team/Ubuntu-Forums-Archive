---
title: "WiFi not working"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by andygeorge on 2007-04-23
Hey folks, I just installed feisty and I'm having trouble getting my wireless card working. On my laptop there's a little light for my wireless device which is always  on; it's not listed as a Network Device on 'Network Tools'.

When I do: sudo lshw -class Network

I get this:

*-network:0 DISABLED
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=64 link=no multicast=yes
       resources: iomemory:d000a000-d000afff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:8b:21:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.7 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0008000-d0008fff irq:10


Can anyone help me please?

---

