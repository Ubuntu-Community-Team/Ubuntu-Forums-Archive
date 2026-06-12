---
title: "No internet on 8.10"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by mtylerb on 2008-11-08
Hey guys, I have a problem getting any internet connection at all.  I *am* using a D-Link (Draft N) router, but it was working fine for 8.04LTS.  Now that I've installed 8.10, it doesn't want to work at all.  I took the router out of the mix and connected directly to the modem with no success.

When I run sudo dhclient eth0 while connected to the modem, I get:

```

~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6174
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:f2:44:8c:f3
Sending on   LPF/eth0/00:15:f2:44:8c:f3
Sending on   Socket fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

This is a fresh install of 8.10 (64-bit), I was trying to fix other issues that cropped up when I upgraded from 8.04 previously by doing a fresh install.  Now I have no internet at all.

Any ideas?

---

### Post by Iowan on 2008-11-08
> **mtylerb said:**
>  I took the router out of the mix and [COLOR="Red"]connected[/COLOR] directly to the modem [COLOR="Red"]with no success[/COLOR]. No success or no problem?

---

### Post by mtylerb on 2008-11-09
No success.  That was right, directly connected to the modem, I am unable to get an IP address.  I'm pretty much a rookie in Linux, I've been using it for the last couple months, but I have been using Windows for the last 18 years or so.  I really am not entirely sure on where to find everything with Linux.  I'm connected with my Windows Laptop right now.

EDIT: I don't know if this means anything, but the /etc/network/interfaces file only has:

```
auto lo
iface lo inet loopback
```

---

### Post by mtylerb on 2008-11-09
Is anybody able to help?  I'd really like to get off the laptop and back on to my PC.  Is there anything I can post here that might help?

---

### Post by mtylerb on 2008-11-09
I managed to get an IP address from my router, but for some reason I still cannot get a website.  I statically setup the eth0 device in /etc/network/interfaces and through the network-manager.  It is able to get an IP address and I can log into the router's admin interface, but still cannot visit external websites.

Anyone have any ideas?

---

### Post by yudelevi on 2008-11-09
check your net settings for a gateway and dns server.
you should set your gateway as the router's IP (so all outgoing traffic goes through the router), also my advice is to show us a trace (try tcpdump) so we can help and decide where the problem occurs.

---

### Post by mtylerb on 2008-11-09
> **yudelevi said:**
> check your net settings for a gateway and dns server.
you should set your gateway as the router's IP (so all outgoing traffic goes through the router), also my advice is to show us a trace (try tcpdump) so we can help and decide where the problem occurs.

Thanks yudelevi.  I went and re-installed using the 32-bit edition instead of the 64-bit edition and the problem went away.  I don't know why it was, but it doesn't really matter now anyway.  I'll try 64-bit at a later date when some of this stuff gets hashed out.

---

### Post by Iowan on 2008-11-09
Connected directly to the modem may require cycling power to the modem (turning it off, waiting 10-15 seconds, then turning it back on).  Some modems seem to "lock onto" the MAC address of whatever is connected to them and won't play nice with anything else with some encouragement.

---

