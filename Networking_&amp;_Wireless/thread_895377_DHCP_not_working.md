---
title: "DHCP not working"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Guruprasad on 2008-08-20
My network card is configured to use DHCP.

It is able to get IP address from the service provider.

But there is no network.

Can anyone help to fix this?

---

### Post by amedac on 2008-08-20
Do you have Intel3945 card?

---

### Post by Guruprasad on 2008-08-20
It is a realtek card. Problem is with eth1, eth0 works fine which is for LAN

ifconfig returned
eth0 Link encap:Ethernet HWaddr 00:13:46:8d:cf:95
inet addr:192.168.100.101 Bcast:192.168.100.255 Mask:255.255.255.0
inet6 addr: fe80::213:46ff:fe8d:cf95/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:244 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:22981 (22.4 KB) TX bytes:5491 (5.3 KB)
Interrupt:16

eth1 Link encap:Ethernet HWaddr 00:80:48:42:d3:ed
inet addr:116.68.64.109 Bcast:255.255.255.255 Mask:255.255.248.0
inet6 addr: fe80::280:48ff:fe42:d3ed/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:882 errors:0 dropped:18454 overruns:0 frame:0
TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:54013 (52.7 KB) TX bytes:4099 (4.0 KB)
Interrupt:17 Base address:0xe400

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:116000 (113.2 KB) TX bytes:116000 (113.2 KB)

sudo ethtool eth1 showed
Settings for eth1:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 32
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pumbg
Wake-on: d
Current message level: 0x00000007 (7)
Link detected: yes


I am using dual boot. THe both networks work fine with windows. So I think there is no problem with cable.

I found the Bcast and Mask for eth1 little odd. Can you please check them?

---

### Post by amedac on 2008-08-20
Your eth0 interface can couse troubles because it have ip adress.
try this: > sudo ifdown eth0
                 sudo ifdown eth1
                 sudo ifup eth1

---

### Post by Guruprasad on 2008-08-21
~$ sudo ifdown eth0



~$ sudo ifdown eth1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5117
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 202.88.238.16 port 67






~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Guruprasad on 2008-08-21
~$ sudo ifdown eth0



~$ sudo ifdown eth1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5117
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 202.88.238.16 port 67






~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Guruprasad on 2008-08-21
~$ sudo ifdown eth0



~$ sudo ifdown eth1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5117
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 202.88.238.16 port 67






~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:48:42:d3:ed
Sending on   LPF/eth1/00:80:48:42:d3:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

