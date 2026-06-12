---
title: "lan not working"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by bebox on 2008-04-25
i had gutsy and my lan worked fine...but now i installed hardy and my lan is not working anymore...when i switch to windows with the same setting it's working...can anybody help me???:confused:

---

### Post by superprash2003 on 2008-04-25
in hardy.. go to the terminal and type ifconfig and post results here

---

### Post by viceroy on 2008-04-25
Post your results of this

```
dmesg | grep eth
```

---

### Post by bebox on 2008-04-25
> **superprash2003 said:**
> in hardy.. go to the terminal and type ifconfig and post results here

eth0      Link encap:Ethernet  HWaddr 00:13:8f:89:7a:fd  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0a:5e:3f:44:d8  
          inet addr:40.30.5.62  Bcast:40.30.5.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65016 (63.4 KB)  TX bytes:65016 (63.4 KB)

---

### Post by bebox on 2008-04-25
> **viceroy said:**
> Post your results of this

```
dmesg | grep eth
```

[   16.294428] eth0: RTL8168b/8111b at 0xffffc200008ae000, 00:13:8f:89:7a:fd, XID 30000000 IRQ 506
[   29.158605] Driver 'sd' needs updating - please use bus_type methods
[   29.559345] eth1:  setting half-duplex.
[   30.322880] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   37.248664] r8169: eth0: link up

---

### Post by superprash2003 on 2008-04-25
are you using eth1 for internet? type ping google.com and post results here

---

### Post by bebox on 2008-04-25
i don't know...i tried both...i think it should be the RTL8168b/8111b one......

---

### Post by bebox on 2008-04-25
someone had the same problem he resolved it with:

For anyone with the same problem, this is what I did:

Run gedit as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local 

Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Restart the computer and that's it!


..but for me it isn't working...:(

---

### Post by bebox on 2008-04-25
also a typed ethtool:

for eth1:

bebox@bebox:~$ sudo ethtool eth1
[sudo] password for bebox: 
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: no

and for eth0:

	Link detected: yes bebox@bebox:~$ sudo ethtool eth0
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
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)

---

### Post by bebox on 2008-04-25
i can't ping my router...

bebox@bebox:~$ ping 40.30.5.100
PING 40.30.5.100 (40.30.5.100) 56(84) bytes of data.
From 40.30.5.62 icmp_seq=1 Destination Host Unreachable
From 40.30.5.62 icmp_seq=2 Destination Host Unreachable
From 40.30.5.62 icmp_seq=3 Destination Host Unreachable
From 40.30.5.62 icmp_seq=4 Destination Host Unreachable
From 40.30.5.62 icmp_seq=5 Destination Host Unreachable
From 40.30.5.62 icmp_seq=6 Destination Host Unreachable
From 40.30.5.62 icmp_seq=7 Destination Host Unreachable
From 40.30.5.62 icmp_seq=8 Destination Host Unreachable
From 40.30.5.62 icmp_seq=9 Destination Host Unreachable

---

### Post by bebox on 2008-04-26
> **superprash2003 said:**
> are you using eth1 for internet? type ping google.com and post results here

i can't ping google...because i can't ping my router...

---

### Post by bebox on 2008-05-01
why is lan not working???i still didnt solve the problem...please..anybody? Destination Host Unreachable?????

---

