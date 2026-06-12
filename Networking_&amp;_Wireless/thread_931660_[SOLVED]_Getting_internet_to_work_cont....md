---
title: "[SOLVED] Getting internet to work cont..."
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Skyker on 2008-09-27
I started the topic here: [http://ubuntuforums.org/showthread.php?t=930644](http://ubuntuforums.org/showthread.php?t=930644)

but no ones seems to understand what's wrong, so I figured I might find some more experienced people here.  Here's the last thing I put in my terminal:

```
kimberley@kimber:~$ sudo ifconfig eth1 up
[sudo] password for kimberley: 
kimberley@kimber:~$ sudo iwconfig eth1 essid "cybercyle"
kimberley@kimber:~$ sudo iwconfig eth1 key 123456789A
kimberley@kimber:~$ sudo iwconfig eth1 mode Managed
kimberley@kimber:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:2d:f6:43
Sending on   LPF/eth1/00:10:a7:2d:f6:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Basically in the past thread we confirmed that my USB device recognizes the wireless router.  But for whatever reason, it doesn't want to connect.

---

### Post by Skyker on 2008-09-27
... Anyone out there that can help me?

---

### Post by superprash2003 on 2008-09-28
you first need to eth1 down not up.. before you configure.. cant you do it via GUI.. system->admin->network->wireless card properties.. disable roaming mode.. try with static ip if dhcp isnt working..

---

### Post by Skyker on 2008-09-28
already done.  and I did do 'down' first, but someone told me to try it like this after that.

---

### Post by Skyker on 2008-09-30
*bump*

---

