---
title: "Ethernet link not detected in ubuntu 14.04 after update"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by usaar33 on 2015-02-08
Since I ran some update in the past week or so, I have not been able to get a wired connection.  Specifically:

[LIST]
[*]Initially, during boot up, the ethernet link light is on
[*]As ubuntu boots up, the link light will go off
[*]Ubuntu reports cable is disconnected
[*]If I boot into Windows 7, I can use the internet without issue.
[/LIST]

My problem is similar to what is described at: [http://askubuntu.com/questions/574433/ethernet-lights-not-on-when-cable-connected-and-not-working#comment807227_574433](http://askubuntu.com/questions/574433/ethernet-lights-not-on-when-cable-connected-and-not-working#comment807227_574433)

lspci entry:

```

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

```

sudo ethtool eth0:
```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no

```

ifconfig -a 
```

eth0      Link encap:Ethernet  HWaddr d4:3d:7e:26:b2:20
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25463 (25.4 KB)  TX bytes:25463 (25.4 KB)

lxcbr0    Link encap:Ethernet  HWaddr 7a:01:dd:5c:17:99  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::7801:ddff:fe5c:1799/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11788 (11.7 KB)

```

syslog:
```

Feb  8 18:20:42 newdesk kernel: [    4.048721] r8169 0000:03:00.0 eth0: link down
Feb  8 18:20:42 newdesk kernel: [    4.048751] r8169 0000:03:00.0 eth0: link down
Feb  8 18:20:42 newdesk kernel: [    4.048760] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb  8 18:20:42 newdesk kernel: [    4.048905] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready


```


As I lack another network card, I can only use windows right now.  Advice on how to fix this is appreciated.

Thanks!

---

### Post by usaar33 on 2015-02-11
Bumping in the hopes that with a new set of eyes, someone will be able to help.

---

### Post by usaar33 on 2015-02-17
Trying again...

---

