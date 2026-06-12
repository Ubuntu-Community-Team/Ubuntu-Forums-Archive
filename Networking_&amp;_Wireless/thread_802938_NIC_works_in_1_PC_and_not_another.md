---
title: "NIC works in 1 PC and not another"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Porwah on 2008-05-21
I have a dual boot machine. I can't get a network connection with on the Ubuntu side.  I'm on the XP side right now and connected fine.  (Would much rather be on the Ubuntu side exploring and checking it out.)

Here's the real killer.  I put the same NIC that I'm on with in XP right now into another machine.  Using the 8.04 Live CD, I can get on fine with it.  No fuss at all.

Here's some command output.

For the machine where the NIC works with the Live CD:
ethtool```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:00:0f.0
```

And ifconfig.
```
eth0      Link encap:Ethernet  HWaddr 00:40:05:34:95:5d  
          inet addr:192.168.11.7  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe34:955d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:248156 (242.3 KB)  TX bytes:36064 (35.2 KB)
          Interrupt:5 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:109300 (106.7 KB)  TX bytes:109300 (106.7 KB)
```

Routes are setup, same with DNS.  Settings are all automatically configured by the Live CD.

On the dual booting machine which also has 8.04 (reinstalled twice) and where the NIC works in XP, here are command results.
ethtool
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes
driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:00:0b.0
```

ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:40:05:34:95:5d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 Base address:0xd800 

eth0:avahi Link encap:Ethernet  HWaddr 00:40:05:34:95:5d  
          inet addr:169.254.5.12  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47784 (46.6 KB)  TX bytes:47784 (46.6 KB)
```

I can't figure this one out.  I'm a newbie.  Can anyone suggest anything?

---

### Post by Porwah on 2008-05-21
I tried the commands in this Sticky to bring the card down and then up again:
```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo dhclient <interface>
```

It's sending the DHCPDISCOVERS and I see in the router log multiple OFFERs with an IP goes out, but the PC doesn't get them.  It results with No DHCPOFFERS received.

Does this help anyone at all?

---

### Post by Iowan on 2008-05-22
Do you power all the way down when switching sides? Another thread suggested that the card doesn't get completely reset unless you do.

---

