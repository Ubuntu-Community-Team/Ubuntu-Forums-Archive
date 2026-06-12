---
title: "Internet Connection in Ubuntu"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by theswan on 2006-10-25
hi everyone. i know this has been asked infinite number of times. sorry, but i can't find any better solution that posting here.

here goes, i installed Ubuntu many months before and go dual boot with windows xp. haven't used Ubuntu much 'cause i don't have internet connection there.

in win xp, you have there the option to automatically get IP and DNS so no need to enter it manually. i think that similar feature is not working in my Ubuntu. :( 

i'm using a broadband connection and i have wire set-up working perfectly fine when in win xp, but not in Ubuntu. It's the same machine, a Toshiba M40 laptop.

when i tried 'sudo pppoeconf' in the terminal i get this message saying that the system has found 2 ethernet interfaces, eth0 and eth1, and asks if these are all the ethernet interfaces i've got..when i click on yes, it scans the eth0 for PPPoe Access Concentrator and PPPoe Access Concentrator (Multi-modem mode). same thing goes for eth1. then, i got the message "sorry, i scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running PPPoe process which controls the modem."

i don't have anymore idea to solve this. :(

---

### Post by theswan on 2006-10-26
anyone please?

after some more readings, i tried the ff:

> theswan@theswan:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:24:59:95
          inet6 addr: fe80::2a0:d1ff:fe24:5995/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:bc000000-0

eth1      Link encap:Ethernet  HWaddr 00:13:CE:27:6E:2F
          inet6 addr: fe80::213:ceff:fe27:6e2f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 Memory:b000b000-b000bfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:762687 (744.8 KiB)  TX bytes:762687 (744.8 KiB)


> theswan@theswan:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:a0:d1:24:59:95
Sending on   LPF/eth0/00:a0:d1:24:59:95
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

> theswan@theswan:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:13:ce:27:6e:2f
Sending on   LPF/eth1/00:13:ce:27:6e:2f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
eDHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

please help. thanks

---

