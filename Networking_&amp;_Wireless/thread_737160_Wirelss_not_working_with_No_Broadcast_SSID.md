---
title: "Wirelss not working with No Broadcast SSID"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by AlanB66 on 2008-03-27
There are a bazillion entries and I'm not sure which covers what, so I'm reluctantly starting a new thread to see if this is the "known" bug or a new one.

Linksys WRT54GL
Compaq F750US
Atheros mini PCI AR5007
Ubuntu 8.04b

I have wireless working so long as my SSID is broadcasting. As soon as I disable broadcast, I'm off the network. But, everthing is stated in the Network Manager, I just want it to find the network specified w/o needing broadcast.

lspci -v:
[INDENT]  03:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>[/INDENT]


ifconfig (eth0 removed from report):
[INDENT]ath0      Link encap:Ethernet  HWaddr 00:1f:a3:52:c1:b0  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:a3ff:fe52:c1b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30198138 (28.7 MB)  TX bytes:1336362 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1417476 (1.3 MB)  TX bytes:1417476 (1.3 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-A3-52-C1-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265379 errors:0 dropped:0 overruns:0 frame:120
          TX packets:15599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:52231879 (49.8 MB)  TX bytes:1824291 (1.7 MB)
          Interrupt:22[/INDENT]


If there is more needed from me, please advise.
If this is associated to a bug already in work, please link.

Thanks for your patience.

---

