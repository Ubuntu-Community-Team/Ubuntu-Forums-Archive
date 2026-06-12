---
title: "dhcp seems to work but I can`t access to internet!"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by flapane on 2007-03-10
/etc/network# dhclient
There is already a pid file /var/run/dhclient.pid with pid 9879
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:01:29:16:27:c6
Sending on   LPF/eth0/00:01:29:16:27:c6
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 39.255.32.40
bound to 39.255.32.43 -- renewal in 1483 seconds.

and that is correct...
resolv.conf also shows the right dns

 ping [www.google.it](www.google.it)
PING [www.l.google.com](www.l.google.com) (209.85.135.99) 56(84) bytes of data.
64 bytes from mu-in-f99.google.com (209.85.135.99): icmp_seq=1 ttl=237 time=68.0 ms
64 bytes from mu-in-f99.google.com (209.85.135.99): icmp_seq=2 ttl=237 time=65.8 ms

it works, too...
But it seems I can-t access to internet! Neither apt-get update works, it says that he cannot resolv packages.ubuntu.com and so on.
I don`t know what to do...

---

### Post by chili555 on 2007-03-10
Probably a DNS nameserver problem. Please let us see cat /etc/resolv.conf.

---

### Post by flapane on 2007-03-11
> **flapane said:**
> 
resolv.conf also shows the right dns


search fastwebnet.it
62.101.81.80
1.253.128.33

---

### Post by chili555 on 2007-03-11
> search fastwebnet.it
62.101.81.80
1.253.128.33

Is the second nameserver a typographical error? 1.253.xx IP addresses are IANA reserved and not pingable. Did you get these from Fastwebnet's DHCP server automatically when you connected or from their website or...?

Let us know.

---

### Post by flapane on 2007-03-11
My isp is behind a NAT, so those ip are pingable only in our ISP and they are given automatically form dhcp and are the same than Windoze
[IMG]http://img403.imageshack.us/img403/3871/ipkx3.jpg[/IMG]

---

### Post by flapane on 2007-03-12
up

---

