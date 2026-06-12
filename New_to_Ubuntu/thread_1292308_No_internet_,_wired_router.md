---
title: "No internet , wired router"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by cookie365 on 2009-10-15
Hi

I'm a total Linux newbie so apologies if this has been answered before.

Just installed 9.04 as sole OS.

My internet is DSL to a cable modem, through a router (netgear wgr614v6). From there it's a wired connection to the Ubuntu PC.

However, when I try to connect to the internet Firefox can't find any website. If I try to connect directly to the router Firefox tells me that the connection was refused.

I'm sure it's not a problem with the modem or router - I'm typing this on a PC connecting wirelessly to the same router, and there isn't any MAC filtering set up.

Do I perhaps need to install chipset drivers for my mobo? It's a Gigabyte GA-M720-US3 which uses nForce 720D.

Thanks

---

### Post by jbrown96 on 2009-10-15
No you shouldn't have to install any drivers. could you post the output from the following commands. Execute them in a terminal: Applications-->Accessories-->terminal. 

```
ifconfig
```
```
sudo lshw -class network
```
Then try to request a ip address with ```
sudo dhclient
```

---

### Post by cookie365 on 2009-10-15
Thank you for taking the time to reply jbrown96 - it's very much appreciated :)

Here's what I get:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:60:03:1d  
          inet6 addr: fe80::224:1dff:fe60:31d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16904 (16.9 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8936 (8.9 KB)  TX bytes:8936 (8.9 KB)
```

sudo lshw -class network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:60:03:1d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:eb:a5:6a:46:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

sudo dhclient
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/32:eb:a5:6a:46:b2
Sending on   LPF/pan0/32:eb:a5:6a:46:b2
Listening on LPF/eth0/00:24:1d:60:03:1d
Sending on   LPF/eth0/00:24:1d:60:03:1d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.3 from 192.168.1.1
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.3 -- renewal in 37938 seconds.
```

Not sure I like the words 'DISABLED' and 'failed' there ;)

Thank you :)

---

### Post by sandyd on 2009-10-15
> **cookie365 said:**
> Hi

I'm a total Linux newbie so apologies if this has been answered before.

Just installed 9.04 as sole OS.

My internet is DSL to a cable modem, through a router (netgear wgr614v6). From there it's a wired connection to the Ubuntu PC.

However, when I try to connect to the internet Firefox can't find any website. If I try to connect directly to the router Firefox tells me that the connection was refused.

I'm sure it's not a problem with the modem or router - I'm typing this on a PC connecting wirelessly to the same router, and there isn't any MAC filtering set up.

Do I perhaps need to install chipset drivers for my mobo? It's a Gigabyte GA-M720-US3 which uses nForce 720D.

Thanks
one line answer today.
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/588366.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/588366.html)

---

### Post by cookie365 on 2009-10-17
Oddly, it just kicked into life half an hour later without any intervention.

Computers ... :confused:   :P

---

### Post by LewRockwell on 2009-10-17
> **carlee said:**
> one line answer today.
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/588366.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/588366.html)

oh carlee, you're so sensible...

lol

.

---

### Post by LewRockwell on 2009-10-17
> **cookie365 said:**
> Oddly, it just kicked into life half an hour later without any intervention.

LAN leases might have expired and the reset provided connectivity

.

---

