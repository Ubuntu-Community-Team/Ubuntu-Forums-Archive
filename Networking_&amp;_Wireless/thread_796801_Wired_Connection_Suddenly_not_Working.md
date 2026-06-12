---
title: "Wired Connection Suddenly not Working"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Etaile on 2008-05-16
Hello, I've been happily using Ubuntu (8.04) for awhile now with a wireless connection from my router, when I decided to buy a cable to hook up (from my router to my computer) for more reliable wired internet. It worked well for about a week and then suddenly it broke, and won't work. (Wireless still works)

INFO:
I choose Wired Internet from the gnome panel and it immediately gets stuck on "Requesting a network address from the wired network..." for about 30 seconds, then says "Wired Internet Connection", and everything looks fine. Turns out nothing works.

ifconfig (I'd assume I'd be using eth0 with wired):
```
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:35:d1:dd  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967030 overruns:0 frame:0
          TX packets:0 errors:0 dropped:184 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:35:d1:dd  
          inet addr:169.254.9.107  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:218 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31300 (30.5 KB)  TX bytes:31300 (30.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:89:90:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2990316 (2.8 MB)  TX bytes:496300 (484.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-89-90-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

dhclient:
```
There is already a pid file /var/run/dhclient.pid with pid 10025
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:1e:8c:35:d1:dd
Sending on   LPF/eth0/00:1e:8c:35:d1:dd
Listening on LPF/wlan0/00:16:44:89:90:b7
Sending on   LPF/wlan0/00:16:44:89:90:b7
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 40071 seconds.


```

/etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

dhclient.eth0.leases:
```
lease {
  interface "eth0";
  fixed-address 192.168.1.102;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 64.59.176.13,64.59.176.15;
  option dhcp-server-identifier 192.168.1.1;
  option domain-name "wp.shawcable.net";
  renew 5 2008/5/16 21:27:55;
  rebind 5 2008/5/16 21:27:55;
  expire 5 2008/5/16 21:27:55;
}
```

dhclient.leases:
```
lease {
  interface "wlan0";
  fixed-address 192.168.1.101;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 86400;
  option routers 192.168.1.1;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.1;
  option domain-name-servers 64.59.176.13,64.59.176.15;
  option domain-name "wp.shawcable.net";
  renew 6 2008/5/17 08:52:48;
  rebind 6 2008/5/17 18:04:23;
  expire 6 2008/5/17 21:04:23;
}
```

Hope something in there helps to solve my problem! Thanks!

---

### Post by Etaile on 2008-05-16
Bump :(

---

### Post by Etaile on 2008-05-16
Still nothing? Wireless sucks :(

---

