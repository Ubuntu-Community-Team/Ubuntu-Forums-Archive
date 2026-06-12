---
title: "Network not connected with 3c905c-TX/TX-M"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by cybertron3000 on 2008-05-11
I installed Ubuntu on an older used model Dell GX50 Optiplex, which has a 3Com 3C905C-TX/TX-M ethernet interface.  Apparently it uses a driver of 3c59x.  

Long to short, Ubuntu works fine, I can enter Firefox,  but it simply says it is unable to connect.  I assume that the install didn't automatically configure my ethernet?  My connection itself is solid, being used by the other functioning desktop that has run Ubuntu with no such problems.

---

### Post by Iowan on 2008-05-12
Post results of **ifconfig** and contents of **/etc/network/interfaces**. I have a GX1, a GX110 and a GX200 which are (or have been) working on my network. I presume one (or all) use the same onboard 3Com NIC.

---

### Post by Nule on 2008-08-18
Hi,

I have been trying to solve this problem for a while but I could not find adequate solution. Please help me. I desperately need to get working my laptop.

This are the results of the following commands:

**ifconfig**



eth0      Link encap:Ethernet  HWaddr 00:e0:91:08:4f:d0  
          inet6 addr: fe80::2e0:91ff:fe08:4fd0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26129 errors:0 dropped:0 overruns:115 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1601738 (1.5 MB)  TX bytes:6377 (6.2 KB)
          Interrupt:11 Base address:0x4800 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:91:08:4f:d0  
          inet addr:169.254.7.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102172 (99.7 KB)  TX bytes:102172 (99.7 KB)


**And content of etc/network/interfaces**

auto lo
iface lo inet loopback

iface eth0inet dhcp
auto eth0

---

### Post by netztier on 2008-08-18
> **cybertron3000 said:**
> I installed Ubuntu on an older used model Dell GX50 Optiplex, which has a 3Com 3C905C-TX/TX-M ethernet interface.  Apparently it uses a driver of 3c59x.  


[COLOR="Gray"][INDENT]The dreaded 3c905 again. See also this post

[http://ubuntuforums.org/showpost.php?p=4381208&postcount=3](http://ubuntuforums.org/showpost.php?p=4381208&postcount=3)

with links to these threads

[http://ubuntuforums.org/showthread.php?t=387839](http://ubuntuforums.org/showthread.php?t=387839)
[http://ubuntuforums.org/showthread.php?t=503194](http://ubuntuforums.org/showthread.php?t=503194)

The reason you're not seeing any link migh be that the 3com card has some internal register bits configured to not autosense the speed nor autonegotiate the ethernet duplex mode.

In general, this can be cured with a DOS-based tool downloadable from 3com (see second thread for download URLs).[/INDENT][/COLOR]

Ah, forget this indented crap  - should've looked at the command output more closely:

> **ifconfig**

eth0 Link encap:Ethernet HWaddr 00:e0:91:08:4f:d0
inet6 addr: fe80::2e0:91ff:fe08:4fd0/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:26129 errors:0 dropped:0 overruns:115 frame:0
TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1601738 (1.5 MB) TX bytes:6377 (6.2 KB)
Interrupt:11 Base address:0x4800

eth0:avahi Link encap:Ethernet HWaddr 00:e0:91:08:4f:d0
inet addr:169.254.7.103 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:11 Base address:0x4800 


There we have it. eth0 has not been given an IP address from a DHCP server - although your config excerpt from /etc/network/interfaces tells it to. Avahi then went ahead and self-assigned a so-called "link local" 169.254.x.x address to this NIC, as per RFC3330.

Is there a DHCP server on your network (commonly, broadband routers have an integrated one), and is it giving out addresses? Are you maybe connecting directly to your broadband modem and your systems get IP addresses assigned directly from your ISP (probably also via DHCP), and the number of addresses that you can get (DHCP-speak: "lease") has been exceeded?


regards

Marc

---

