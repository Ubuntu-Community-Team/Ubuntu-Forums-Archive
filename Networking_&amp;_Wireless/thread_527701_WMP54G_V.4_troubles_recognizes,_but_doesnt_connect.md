---
title: "WMP54G V.4 troubles: recognizes, but doesnt connect"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by mcg1sean on 2007-08-16
Ok, so Ive installed a fresh copy of 7.04. Ive got a linksys WMP54G V.4 wireless card. Ubuntu sees the card and all, but when I tell it to connect to my home network, it doesnt. It can see the network but just cant connect. The network has WPA encryption (the router is a Linksys WRT54G). Ive tried it with and without the encryption but still doesnt work. What do I do? Ive searched the forums and havent really found anything that is exactly related to the problem that I am having.

---

### Post by fredj on 2007-08-17
Can you open a terminal and type sudo lshw -class network and post the output from that here.

---

### Post by mcg1sean on 2007-08-20
ok this is what I got when I typed what you told me to into the terminal

 *-network                
       description: Ethernet interface 
       product: nForce2 Ethernet Controller 
       vendor: nVidia Corporation 
       physical id: 4 
       bus info: pci@00:04.0 
       logical name: eth0 
       version: a1 
       serial: 00:e0:4c:db:8b:8a 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII 
       resources: iomemory:e0000000-e0000fff ioport:d000-d007 irq:18 
  *-network 
       description: Wireless interface 
       product: RT2500 802.11g Cardbus/mini-PCI 
       vendor: RaLink 
       physical id: 8 
       bus info: pci@01:08.0 
       logical name: ra0 
       version: 01 
       serial: 00:0c:41:6c:3c:2f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=32 link=yes multicast=yes wireless=RT2500 Wireless 
       resources: iomemory:df000000-df001fff irq:19

---

