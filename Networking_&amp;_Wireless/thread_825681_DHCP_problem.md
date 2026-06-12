---
title: "DHCP problem ?"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by -p-u-r-g- on 2008-06-11
I have a very weird problem with my internet connection...
I can't connect to internet (wired) through the modem in kubuntu (in windows xp it works fine) but it works when I connect through my router.

It's not actually a problem because I can use the router anyway, but I just want to know why it won't connect directly.

Here's my ifconfig -a :
> eth0      Link encap:Ethernet  HWaddr <myMACADDRESS>
          inet6 addr: fe80::21d:7dff:fe9b:2267/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4447222 (4.2 MB)  TX bytes:658564 (643.1 KB)
          Interrupt:219 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19796 (19.3 KB)  TX bytes:19796 (19.3 KB)
 

Here is the result of /etc/initnd/networking restart   :
>  
* Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:7d:9b:22:67
Sending on   LPF/eth0/00:1d:7d:9b:22:67
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/<myMACADDRESS>
Sending on   LPF/eth0/<myMACADDRESS>
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and  dmesg  says :
> [10671.457673] r8169: eth0: link up
[10681.811275] eth0: no IPv6 routers present


if that is of any help...

---

### Post by superprash2003 on 2008-06-11
is DHCP enabled in your modem?

---

### Post by -p-u-r-g- on 2008-06-11
Oh, I forgot to add... Another computer, also running Kubuntu (same version) works just fine directly through the modem (as did this one until recently)...

Oh yeah, and the modem is actually a switch for optics...

---

