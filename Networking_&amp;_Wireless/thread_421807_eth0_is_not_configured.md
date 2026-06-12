---
title: "eth0 is not configured?"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jlist on 2007-04-24
I just installed ubuntu 7.04 desktop on vmware, and copied the vm to another PC, both running windows XP as vmware host OS. The eth0 interface is not configured on the second copy, eth1 seems to be working fine. Any idea why it's eth1 instead of eth0?

Here's my interface file
```
root@ubuntu:~# cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

Here's ifdown output:
```

root@ubuntu:~# ifdown eth0
ifdown: interface eth0 not configured
```

Here's ifconfig output:
```

root@ubuntu:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0C:29:FD:E6:94  
          inet addr:192.168.8.156  Bcast:192.168.9.255  Mask:255.255.254.0
          inet6 addr: fe80::20c:29ff:fefd:e694/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9837241 (9.3 MiB)  TX bytes:347605 (339.4 KiB)
          Interrupt:17 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:604 (604.0 b)  TX bytes:604 (604.0 b)
```

---

### Post by Floppyjoe on 2007-04-24
Eth0 is usually a wired interface. Sometimes eth1 is a wireless interface. The VM was configured on one computer and then moved to another. Is the second computer set up exactly the same as the first one?

---

### Post by jlist on 2007-04-24
Both PCs are laptops, both have a wired and wireless connection. When the vm is installed on the first PC, only wireless is used. On the second PC, both wired and wireless are connected.

---

