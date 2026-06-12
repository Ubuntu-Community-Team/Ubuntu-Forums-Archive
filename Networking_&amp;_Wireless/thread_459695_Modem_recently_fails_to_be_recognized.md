---
title: "Modem recently fails to be recognized"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by nekator on 2007-05-30
OK I am running ubuntu Dapper Drake on my home dual boot PC...Unfortunately I am currently using WXP to send this post. Seems like Ubuntu decided not to recognize my Motorola broadband modem this morning, same PC but WinXp working fine (well, as fine as WinXp will). After screeming at the ISP technical support folks for not having internet I sudeenly realiza WinXp is fine with internet....I have tried all sorts of things recommended herein...but have gone nowhere....My Ubuntu guru says perhaps I should wait it out (HuH?): anyways...here's additional info that might be of use to you hardcore Ubuntuist.

First, running network restart

nekator@nekator-desktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:ec:b7:4b:41
Sending on   LPF/eth0/00:16:ec:b7:4b:41
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.52.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:ec:b7:4b:41
Sending on   LPF/eth0/00:16:ec:b7:4b:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.54.12.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.54.12.1
SIOCADDRT: Network is unreachable
bound to 10.54.12.63 -- renewal in 20193 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


Then running Ifconfig

nekator@nekator-desktop:~$ ifconfig #
eth0      Link encap:Ethernet  HWaddr 00:16:EC:B7:4B:41
          inet addr:10.54.12.63  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::216:ecff:feb7:4b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:484660 (473.3 KiB)  TX bytes:1152 (1.1 KiB)
          Interrupt:209 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

finally

nekator@nekator-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

nekator@nekator-desktop:~$


Please help me, I try to get on and work with ubuntu and learn as much as I can but this is my home PC and it took a lot of time and almost a divorce to get the children and wifey to accept Ubuntu into our house...Please help...anything will do.

Best regards.

---

### Post by nekator on 2007-06-05
Well, well, well, What do you know? The goddamn bug reverted to normality on its own this morning? So now I am happy,not thanks to anyone. So its true, if you leave ubuntu throw a fit on its own, like a child (more later than sooner) it will revert to normality...Undependable however, I'm scrapping this OS and heading for redhat. Best.

---

