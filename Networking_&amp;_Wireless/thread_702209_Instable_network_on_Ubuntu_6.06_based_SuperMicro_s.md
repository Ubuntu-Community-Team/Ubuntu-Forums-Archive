---
title: "Instable network on Ubuntu 6.06 based SuperMicro server"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by fvlasveld on 2008-02-20
Hello all,

I'm having a strange problem with a new SuperMicro 5015MT+ server. I recently installed Ubuntu 6.06 on this server (not the LAMP version, but I manually added Mysql, Proftpd, Bind, Postfix, Apache, PHP, Courier-POP3/Courier-IMAP and ISPConfig). When working from the office network, the server responded very fast to network traffic such as HTTP or SSH. However, I yesterday installed the server in a data center, and since then, connecting to the machine is -very- unstable. Sometimes I'm able to connect to it, sometimes I'm not (it just doesn't respond then).

On this server there are two network interfaces. One of them is connected to the internal VLAN, and the other is pretty directly connected to the outside world. Whenever I'm unable to connect to the server using the outside IP, I login to another machine on the internal VLAN and try to connect to the internal IP. That works, most of the time.

Whenever I "/etc/init.d/networking restart", the connection becomes available quite stable for a few minutes, but then after a while it gets unstable again. Nothing seems to be wrong with the actual NIC though, because I'm able to download skype.exe (as a test file) with over 10 mbit/s. 

Here is my interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 80.xx.xx.70
 netmask 255.255.255.128
 gateway 80.xx.xx.1
 broadcast 80.xx.xx.255

auto eth1
iface eth1 inet static
 address 10.0.0.70
 netmask 255.255.255.0
 gateway 10.0.0.1
 broadcast 10.0.0.255
```

This is the current output of ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:30:48:96:B1:20  
          inet addr:80.xx.xx.70  Bcast:80.xx.xx.255  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:24130214 (23.0 MiB)  TX bytes:533361 (520.8 KiB)
          Base address:0x5000 Memory:e8a00000-e8a20000 

eth1      Link encap:Ethernet  HWaddr 00:30:48:96:B1:21  
          inet addr:10.0.0.70  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:70289 (68.6 KiB)  TX bytes:308918 (301.6 KiB)
          Base address:0x6000 Memory:e8b00000-e8b20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7335 (7.1 KiB)  TX bytes:7335 (7.1 KiB)
```

I disabled IPv6, just to see if that makes any differences. Unfortunately, it doesn't seem to change the behavior. Also, I gave the server another IP just to see if that would make the problem disappear.. As you probably guessed, it didn't. In the hosting rack, I have a number of other SuperMicro servers running a home brewn LFS Linux that work just fine (for years already). Also, I have an identical SuperMicro machine (in another data center) with Ubuntu 6.06 running VMware that doesn't have any problems. 

What could the problem be? Any thoughts on this? 

Thanks!

---

### Post by fvlasveld on 2008-02-21
Some extra information, here is the output of "lshw -C network":

```
*-network               
       description: Ethernet interface
       product: 82573E Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0d:00.0
       logical name: eth0
       version: 03
       serial: 00:30:48:96:b1:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e1000 driverversion=7.0.33-k2 duplex=full firmware=0.15-4 ip=80.69.93.70 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e8a00000-e8a1ffff ioport:5000-501f irq:66
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0e:00.0
       logical name: eth1
       version: 00
       serial: 00:30:48:96:b1:21
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e1000 driverversion=7.0.33-k2 duplex=full firmware=0.5-7 ip=10.0.0.70 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e8b00000-e8b1ffff ioport:6000-601f irq:74
```

And, the output of "ethtool eth0" and eth1:

```
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
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

Settings for eth1:
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
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes

```

---

### Post by fvlasveld on 2008-02-24
Ehm.. any ideas on this one?

---

### Post by fvlasveld on 2008-02-24
Just to keep you up-to-date: Nick from the ubuntu user technical support mailing list answered my question there regarding this problem:

[I]I have similar SuperMicro servers with no issues.  I'd look first at the 
switch this server is connect to and make sure the ports are set to auto 
negotiate just like your interfaces are.  If they are set to auto 
negotiation, then I'd force them to 100/full and do the same to your 
server's network cards.  I've seen speed/duplex mismatches cause lots of 
odd problems before.

Aside from that, I'd be looking for hardware issues.  See anything odd 
in the logs?[/I]

I've first of all forced eth0 (the 'external' interface) to operate at 100/Full. However, that didn't stop the problem. I then changed the settings so that eth0 was allowed to negotiate, but only up to 10/Full. Unfortunately, this didn't solve the problem as well. At this time, I'm not able to force the 3com switch to operate at 100/full only. However, it should be able to handle both 100/full and 10/full perfectly.

Output of ethtool eth0 at this time:

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full
	                        100baseT/Half 100baseT/Full
	                        1000baseT/Full
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Full
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
```

Hardware issue is of course always possible. However, since both eth0 and eth1 display this problem, that seems quite unlikely.

Does anybody else have any other suggestions?

---

### Post by fvlasveld on 2008-02-26
Finally, I solved the problem!! With the help of Aart from the Ubuntu users mailing list, I found out that I had TWO default routes defined! Removing one of them by removing one gateway from the interfaces file solved the problem. Small solution for a not so big problem after all.

---

