---
title: "Ubuntu not recognizing my modem"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by nekator on 2007-05-31
I use Dapper drake at home and two days ago Ubuntu stopped recognizing my ADSL cable modem which used to work fine previously and which still does when I boot the same PC Ubuntu is on with WinXP (hate to admit it but no other way of getting to the internet). I REALLY NEED HELP ! Noone seems to be reading or posting replies...This is what I have been getting through ifconfig # both before and after /etc/init.d/networking restart

nekator@nekator-desktop:~$ ifconfig #
eth0      Link encap:Ethernet  HWaddr 00:16:EC:B7:4B:41
          inet addr:10.54.12.63  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::216:ecff:feb7:4b41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:642379 (627.3 KiB)  TX bytes:1152 (1.1 KiB)
          Interrupt:209 Base address:0x6c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

AND THIS IS WHAT I GET WHEN I DO THE NETWORKING RESTART THINGYMAGIG

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
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.54.12.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.54.12.1
SIOCADDRT: Network is unreachable
bound to 10.54.12.63 -- renewal in 22537 seconds.
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


AND FINALLY, THIS IS WHAT I GET AFTER ps aux | grep dhclient #

nekator@nekator-desktop:~$ ps aux | grep dhclient #
dhcp      5725  0.0  0.1   2340   540 ?        Ss   02:28   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
nekator   5832  0.0  0.1   2888   816 pts/0    S+   02:29   0:00 grep dhclient


I really need help on this one...should I try to upgrade to 7 to see if that will solve things, should I try to reload 6? Will I loose my preferences and desktop and other crap? Sht...Terrible mood...this shouldnt be happening, I have touched nothing! Perhaps some recent update that I installed?
Please help1

---

### Post by nekator on 2007-06-01
Anyone...? This is so frustrating...even MS WinXP out does Ubuntu on this one...what a shame, might have to go back to using that crap OS again...

---

### Post by nekator on 2007-06-05
Well, well, well, What do you know? The goddamn bug reverted to normality on its own this morning? So now I am happy,not thanks to anyone. So its true, if you leave ubuntu throw a fit on its own, like a child (more later than sooner) it will revert to normality...Undependable however, I'm scrapping this OS and heading for redhat. Best.

---

