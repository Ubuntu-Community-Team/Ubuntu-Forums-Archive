---
title: "Server network no link"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by starling on 2008-10-14
Just installed 8.04 server on my old desktop box. The network card was working when I stopped using it a few months back under 7.10 (desktop), but not now.

The card doesn't even get a link light up. I changed the PCI slot, not change. I got another card from an extinct computer which I assume works and it gets a link light on the router, but nothing more. And even then only if it is plugged in after the machine is turned on.

So some outputs for your perusal:

lshw -C network (the first is the older card I'm currently trying to make work. I gave it the IP, but that didn't help)
```
  *-network:0
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 00
       serial: 00:02:e3:13:24:2c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.100 latency=32 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:17:3f:09:ca:ef
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:17:3f:09:ca:ef  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:02:e3:13:24:2c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe13:242c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:541 (541.0 B)  TX bytes:4729 (4.6 KB)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 B)  TX bytes:560 (560.0 B)

```

Current /etc/network/interfaces
```
auto eth1
iface eth1 inet static
	address 192.168.0.100
	subnet 255.255.255.0
	gateway 192.168.0.1
```
I also tried it with "iface eth0 inet dhcp"

Router does DHCP duties with other computers no worries. Cable is fine, router ports are fine.

Interestingly, even with the auto eth1, the interface is disabled by default.
Should also mention I got the realtek (eth0) card working earlier. It did apt-get and I saw apache from another computer, ssh as well. It had a static IP but I don't remember what else I had done and can't seem to repeat it :(

---

### Post by starling on 2008-10-14
oh, and "dhclient eth1" gives the 'unreachable' timeout error.

---

### Post by starling on 2008-10-14
Oh. Don't I look silly.
I missed the critical step I did last time of moving the NIC to another slot. Must be a bit of dust in some of the slots, but working now. Thanks for reading at least :)

---

### Post by Iowan on 2008-10-14
Glad we could all be so much help :confused:
If you're convinced that your problem is [SOLVED], mark the thread accordingly (under Thread Tools). Congrats!

---

