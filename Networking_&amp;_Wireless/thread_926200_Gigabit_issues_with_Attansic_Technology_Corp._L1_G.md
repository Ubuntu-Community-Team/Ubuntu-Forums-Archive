---
title: "Gigabit issues with Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048]"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by odinb on 2008-09-21
Hi!

My Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] will only connect at 100MB/s, even if the switch is Gigabit!

I have several other computers running Ubuntu Hardy, and they all connect at Gigabit speeds, but not this one.

Have tried to force it to Gigabit, but no success:

brodersen@ubuntu-htpc:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok
brodersen@ubuntu-htpc:~$ sudo mii-tool -F 1000baseTx-FD
Invalid media specification '1000baseTx-FD'.

and:

rodersen@ubuntu-htpc:~$ sudo ethtool -s eth0 speed 1000 duplex full
brodersen@ubuntu-htpc:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: d
	Link detected: yes

Cannot see any errors for this card, so cable should be ok:
ifconfig -a eth0
eth0      Link encap:Ethernet  HWaddr 00:1d:60:96:xx:xx  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe96:59d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1776 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1930051 (1.8 MB)  TX bytes:282872 (276.2 KB)

Do I have a driver problem, or what is going on here?

//Odin


Other info:

Hardware info:
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8226]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 220
	Region 0: Memory at dbfc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at dbfa0000 [disabled] [size=128K]
	Capabilities: <access denied>

Hardware status:
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:1d:60:96:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A ip=192.168.1.60 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s

and:

sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: d
	Link detected: yes

---

### Post by odinb on 2008-09-29
Guess I am the only "geek" with a gigabit backbone at home and this network card......

---

### Post by Rinke on 2008-10-01
Same problem here.
I've also tried many things like:
sudo ethtool -s eth0 autoneg off speed 1000 duplex full
sudo ethtool -s eth0 autoneg on speed 1000 duplex full

After either of the above commands "sudo ethtool eth0" results in 
Speed: Unknown!
Duplex: Unknown!

Autonegotiation is allways on, no matter if I set it on or off with speed 1000.

I only get it working for speed 100 but I also have more PC's with Gigabit network cards and a Gigabit switch so I really want this to be working.

My specs:
Ubuntu 8.04 Hardy Heron amd64 (64-bit)
Linux kernel 2.6.24-19-generic
Memory: 4GB RAM
Motherboard: ASUS P5K

---

### Post by Rinke on 2008-10-01
Did you check this thread:
[http://ubuntuforums.org/showthread.php?t=770173]("http://ubuntuforums.org/showthread.php?t=770173")
Ethernet controller: Attansic Technology Corp. Unknown device

We have another problem (set speed to 1000 fails), but we might have an outdated driver.

---

### Post by Rinke on 2008-10-01
I went through the installation of the l1e_l2e-linux-v1.0.0.4 version -> was not compatible with my network card.

The 2.1.3 version works with my network card and is probably allready part of the 2.6.24 linux kernel, but is unable to be set to speed 1000.

On [http://atl1.sourceforge.net/]("http://atl1.sourceforge.net/") I found the following:

*There is a bug in the driver that causes memory corruption during the shutdown of the interface if and only if you have 4GB or more RAM in your system (and your system utilizes all that memory). The bug has been solved and is in the process of being incorporated into kernel 2.6.26. It has been backported to 2.6.25.*

I do have 4GB of RAM but it is not full utilized.
Is the problem of not being able to set speed to 1000 related to this?
Do I have to go through a kernel upgrade from 2.6.24 to 2.6.26?
Is it solved in the next Ubuntu release (8.10)?

---

### Post by odinb on 2008-10-08
> **Rinke said:**
> 
Is it solved in the next Ubuntu release (8.10)?

I guess we will have to wait a couple of more weeks and see, or load the beta....

Need XBMC to support Intrepid before I can upgrade...

---

### Post by hkazmi on 2008-11-12
Just so you know this is not a Ubuntu only issue. I have a dual boot system and the damn Attansic L1 refuses to connect at 1000mbps on either XP or Ubuntu.

Mine was a integrated nic, I called Asus and they couldn't solve the problem. During the debug, I also read somewhere the problem is more with netgear switches and this nic.

One suggestion that seems to work is power cycling the switch itself.

---

### Post by Rinke on 2008-11-13
> **hkazmi said:**
> Just so you know this is not a Ubuntu only issue. I have a dual boot system and the damn Attansic L1 refuses to connect at 1000mbps on either XP or Ubuntu.

Mine was a integrated nic, I called Asus and they couldn't solve the problem. During the debug, I also read somewhere the problem is more with netgear switches and this nic.

One suggestion that seems to work is power cycling the switch itself.


If the combination of switch and nic is the problem: I use the ASUS GigaX1105N switch, is also ASUS so I suppose that should work?

What do you mean with "power cycling the switch itself"?

---

### Post by Rinke on 2008-11-14
Fixed!

Changed 3 things at a time, so I'm not sure which one did the trick.
DualCore -> Core 2 Quad processor
4GB -> 8GB memory
6 meter Cat5E UTP cable custom-made -> new 2 meter Cat5E UTP cable prefabricated

I suppose the cable was the one, but it might also be the memory.
Read somewhere Attansic L1 and 4GB memory can also make problems.

Can't do the check now, but I'll check the speed with the old cable sometime and let you know.

---

### Post by odinb on 2008-11-24
Just upgraded to Intrepid, and still same story, 100Mbit only...

Tried powercycling the switch (Netgear GS116), no difference.
Swapped the cable to CAT6 (old one was CAT5e), no change.
I do have 4GB of RAM, but problem was there when I had 2GB of RAM also.
I do have a Quadcore CPU, have had that all along on this motherboard.

Anyone have any idea how/when this will be fixed?

---

### Post by ian dobson on 2008-11-24
Hi,

Try a different switch/cable, GBit is very sensitive to network cables. I have exactly same card and:-

```

lshw -C network
  *-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: b0
       serial: 00:1a:92:bd:06:b1
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.0.1 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=1GB/s

```

Running 64bit 8.10 on a Q6600 with 4Gb ram.

The 4Gb problem was solved about 8months ago. The problem was that if you had 4Gb or more memory, DMA from the network card "could" overwrite memory above the 4Gb.

Regards
Ian Dobson

---

### Post by odinb on 2008-11-29
Thanks Ian!

You made me check my cables yet another time, and it was a damaged cable!

Now it syncs at Gigabit!

//Odin

---

