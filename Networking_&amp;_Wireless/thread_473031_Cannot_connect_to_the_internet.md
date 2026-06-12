---
title: "Cannot connect to the internet"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Wally Paulnuts on 2007-06-13
I am set up for dhcp and here is what i get when i do an ifconfig -a as instructed by someone on the board....


eth0 Link encap:Ethernet HWaddr 00:02:A5:1E:CC:95
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet HWaddr 00:02:A5:1E:CC:95
inet addr:169.254.7.192 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:72 errors:0 dropped:0 overruns:0 frame:0
TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5296 (5.1 KiB) TX bytes:5296 (5.1 KiB)


anyone with any thoughts on how i can connect to the internet ?

---

### Post by chili555 on 2007-06-13
Please tell me what happens when you complete these commands in order:```
sudo ifdown eth0
sudo /etc/init.d/avahi-daemon stop
sudo ifup eth0
```Thanks.

---

### Post by Wally Paulnuts on 2007-06-13
this is the data that was produced when i input the commands:

anthony@anthony-desktop:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5633
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:1e:cc:95
Sending on   LPF/eth0/00:02:a5:1e:cc:95
Sending on   Socket/fallback
anthony@anthony-desktop:~$ sudo /etc/init.d/avahi-daemon stop
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
anthony@anthony-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:1e:cc:95
Sending on   LPF/eth0/00:02:a5:1e:cc:95
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

