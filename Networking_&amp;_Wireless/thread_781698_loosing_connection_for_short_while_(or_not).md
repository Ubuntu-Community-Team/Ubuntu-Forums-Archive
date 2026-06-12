---
title: "loosing connection for short while (or not?)"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by r1pcurl on 2008-05-04
First of all, sry on my english :)

Now, for the issue... i have problem in my internet connection... any couple of minutes... the firefox just stop to surf, and the Synaptic cant install softwares. But, my xchat keep to be a LIVE and also my Pidgin.
all of this to short time... and then its come back to be normal situation...

Ubuntu Version: 8.04 LTS Desktop Version

i connect with DHCP... i have router: ASUS AM 604g

This is my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:11:d8:34:b3:21
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe34:b321/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:220660408 (210.4 MB)  TX bytes:12367213 (11.7 MB)
          Interrupt:18 Base address:0x9800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:136900 (133.6 KB)  TX bytes:136900 (133.6 KB

You can see that my eth0 dont know any normal ip... (outside...)

I have also try to do the dhclient command here is the output:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:d8:34:b3:21
Sending on   LPF/eth0/00:11:d8:34:b3:21
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.0.0.1 from 10.0.0.138
DHCPREQUEST of 10.0.0.1 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.1 from 10.0.0.138
bound to 10.0.0.1 -- renewal in 37694 seconds.

Very Very Tnx For helpers :)

---

