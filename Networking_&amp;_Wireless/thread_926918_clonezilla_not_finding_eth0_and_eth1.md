---
title: "clonezilla not finding eth0 and eth1"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by Fire_Missionary on 2008-09-22
Hey I've gotten Clonezilla and DRBL running on this machine and when I'm running the drblpush to configure the server I'm running into a snag.

The drblpush is not finding both eth0 and eth1 and as far as I know they should be working correctly.
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:e1:9f:61  
          inet addr:10.0.192.128  Bcast:10.0.192.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee1:9f61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8381 (8.1 KB)  TX bytes:4817 (4.7 KB)
          Interrupt:17 Base address:0x1400 

eth1      Link encap:Ethernet  HWaddr 00:0c:29:e1:9f:6b  
          inet6 addr: fe80::20c:29ff:fee1:9f6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:468 (468.0 B)
          Interrupt:18 Base address:0x1480 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14548 (14.2 KB)  TX bytes:14548 (14.2 KB)

```
DRBL error message when running drblpush -i
```
------------------------------------------------------
Found private IP "10.0.192.128" in eth0 on your system!
Configured ethernet card(s) found in your system: eth0 
------------------------------------------------------
The public IP address of this server is NOT found.
Which ethernet port in this server is for public Internet accsess, not for DRBL connection ?
Available ethernet ports in this server:
eth0 (10.0.192.128), 
[eth0] 
The ethernet port you choose for the WAN connection: eth0
The ethernet port(s) for DRBL environment:   
No ethernet port is available for DRBL environment!
We can NOT continue...

```

Also I manually set up /etc/network/interfaces to be the following:
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

iface eth1 inet static
address 10.0.253.10
netmask 255.255.255.0
```

Any ideas on what to do to fix this?

Thanks in advance.

---

### Post by Fire_Missionary on 2008-09-22
I disabled ipv6, added "auto eth1" and network and broadcast lines to /etc/network/interfaces

also ran " sudo /etc/init.d/networking restart "

Fixed this problem

---

