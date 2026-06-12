---
title: "Non working internet on a Toshiba Satellitte A45-S121"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by mongoos3 on 2007-12-05
I recently installed Ubuntu 7.10 on a friends Toshiba Satellite A45-S121 and as yet have no internet connectivity, i have tried several solutions from other threads but so far nothing has worked.
I am not very good with networking so I'm not able to decipher this,

```
ben@MC1:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0D:EB:0C:CB  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286044 (279.3 KB)  TX bytes:8925 (8.7 KB)

eth0:avah Link encap:Ethernet  HWaddr 00:08:0D:EB:0C:CB  
          inet addr:169.254.7.11  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10080 (9.8 KB)  TX bytes:10080 (9.8 KB)



ben@MC1:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5748
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:0d:eb:0c:cb
Sending on   LPF/eth0/00:08:0d:eb:0c:cb
Sending on   Socket/fallback
ben@MC1:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:08:0d:eb:0c:cb
Sending on   LPF/eth0/00:08:0d:eb:0c:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I'm currently setup for DCHP and passing acpi=noirq at boot, (these items are easily reversed I just haven't done so yet)

Any help with this would be appreciated, thank you.

---

