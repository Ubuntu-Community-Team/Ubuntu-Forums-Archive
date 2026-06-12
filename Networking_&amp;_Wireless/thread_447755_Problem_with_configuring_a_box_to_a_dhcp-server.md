---
title: "Problem with configuring a box to a dhcp-server"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by vsoemlio on 2007-05-18
I have configured a dhcp-server with this settings. The DHCP-Server is listeing on eth0.

> **dhcpd.conf]ddns-update-style none said:**
> 

[quote=ifconfig]eth0      Link encap:Ethernet  HWaddr 00:C1:26:10:21:46
          inet addr:10.0.0.0  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c1:26ff:fe10:2146/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:53422 (52.1 KiB)  TX bytes:3170 (3.0 KiB)
          Interrupt:169 Base address:0xb000

eth1      Link encap:Ethernet  HWaddr 00:16:EC:3A:F6:6F
          inet addr:192.168.0.124  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe3a:f66f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13718 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22485241 (21.4 MiB)  TX bytes:1520075 (1.4 MiB)
          Interrupt:193 Base address:0xe800


My point is: I want to use the box as a router.

This is how I want it

[img]http://img501.imageshack.us/img501/9061/sharebothrg2.jpg[/img]

---

### Post by veloce on 2007-05-19
> **vsoemlio said:**
> I have configured a dhcp-server with this settings. The DHCP-Server is listeing on eth0.





My point is: I want to use the box as a router.

This is how I want it

[img]http://img501.imageshack.us/img501/9061/sharebothrg2.jpg[/img]

Looks more like a firewall set up to me.  Why not just use a little firewall distro like IPCop or pfsense?  I know they aren't Ubuntu, but why install more than you need?  

both these distros give you a nice web interface that allows you to set up your dhcp server simply and easily.

---

