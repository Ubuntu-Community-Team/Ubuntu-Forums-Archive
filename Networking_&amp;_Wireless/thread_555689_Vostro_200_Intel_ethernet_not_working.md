---
title: "Vostro 200 Intel ethernet not working"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by egalitarian on 2007-09-20
OK, I made a minor error installing 7.04 to this box. I installed the 32-bit desktop version, when the PC can handle 64-bit.
uname -r
2.6.20-15-generic

Having said that, I am unable to reach the internet, ping, or otherwise get eth0 up and running.

My setup (some outputs may be truncated since I'm hand transcribing them]:

sudo ifup eth0

```

eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/ 

```

ifconfig -a
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:864 (864.0 b)  TX bytes:864 (864.0 b)

```

sudo lshw -C network

```

*-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:fdfc0000-fdfdffff iomemory:fdfff000-fdffffff ioport:ff00-ff1f irq:10

```

lspci -vv
```

...
00:19.0 Ethernet controller: Inel Corporation Unknown device 10c0 (rev 02)
	Subsystem: Dell Unknown device 0238
	Control: I/O+ Mem+ BusMaster+ ...
	Region 0: Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at fdfff000 (32-bit, non prefetchable) [size=4K]...

```


/etc/network/interfaces
```

auto lo
iface lo inet loopback

```

tail -25 /var/log/kern.log
```

  . . .
...] NET: Registred protocol family 31
  . . .
...] NET: Registered protocol family 10
...] lo: Disabled Privacy Extensions
-------------- the above 2 lines are the last 2 lines

```

Can anybody tell me how to get this ethernet card running?
Thanks

---

### Post by noob12 on 2007-09-20
Yes.  Read this posting [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

---

