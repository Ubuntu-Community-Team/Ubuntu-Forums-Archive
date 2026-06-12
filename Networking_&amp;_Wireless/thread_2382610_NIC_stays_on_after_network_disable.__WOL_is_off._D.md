---
title: "NIC stays on after network disable.  WOL is off. Dell E5570"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by tuxtendo on 2018-01-15
Hi all,

I got an odd bug on my dell latitude E5570 laptop with 16.04.3, using everything stock with Unity. 

After the recent dell bios update of 27 December 2017 (due to the Intel bug) I noticed that my onboard nic wont really go offline. 

Perhaps this was before the bios update also, I don't know for sure because I did not look at my network switch before, its located under my desk.

Let me describe precise what I mean:

When the network is up and running I right click on the network manger icon and click **Enable Networking**. 

The network goes then down -> nic goes down also on the switch but after about 3 seconds it comes back up I can see on the switch. It wont stay off. Ifconfig shows its off, ethtool shows it also.

I made sure that WOL is off with ethtool and its also off in the bios.

This is my ethtool output when then network is down:

```

Settings for enp0s31f6:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown (auto)
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
			       drv probe link
	Link detected: no

```

Its an intel nic:

```

00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-LM (rev 21)
	Subsystem: Dell Ethernet Connection I219-LM
	Flags: bus master, fast devsel, latency 0, IRQ 131
	Memory at e1200000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

```

I did a clean install of Ubuntu a couple of times, and also put Windows 10 temporally back and disabled everything WOL related and power related to the nic off in Windows. 

But it still wont really go down :???:


Anybody got a clue how to make this nic really go down?

---

