---
title: "can't connect to wireless network in Intrepid"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by gravyflex on 2008-11-09
I am unable to connect to my wireless network since I upgraded to intrepid.

I am able to get an ip address from my dhcp server by doing dhclient eth1.

When I right click the knetworkmanager icon I am able to see my ap but when it is selected nothing happens.

So far I am unable to see any events in the system logs.

I am uncertain as to how to proceed with troubleshooting this issue. 

```

sudo lshw -C network
  *-network                        
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation         
       physical id: 1                   
       bus info: pci@0000:02:01.0
       logical name: eth2
       version: 78
       serial: 00:08:74:06:5d:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=halflatency=80 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: RoamAbout 802.11 DS
       product: Version 01.01
       vendor: Enterasys
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:01:f4:75:19:54
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 ip=192.168.1.50 link=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 22:db:98:fb:cc:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

