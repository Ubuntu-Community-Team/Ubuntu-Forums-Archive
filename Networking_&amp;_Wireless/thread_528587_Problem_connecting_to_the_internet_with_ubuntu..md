---
title: "Problem connecting to the internet with ubuntu."
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Devake on 2007-08-18
Hi,

i've just started with linux and have installed Ubuntu 7.10.
everything seems to be ok except the internet connection.........

i followed the ubuntu documentation on configuring pppoe and everything seems to be in place.
however, i cant seem to access the internet via firefox or using the ping command in the terminal.

i did pon dsl-provider, and used dhclient to see if it will help
i got: 

```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp

Listening on LPF/eth0/00:00:39:e8:81:ea
sending on LPF/eth0/00:00:39:e8:81:ea
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.1668.2.2 -- renewal in 6 seconds.

```

pinging to 192.168.2.1 seems to work fine
but pinging to [www.google.com](www.google.com) gets a unknown host response.

does anything have any idea how to fix this?

i'm behind a Arescom NetDSL 800 series DSL modem without a router.

Thank you for all the help

---

