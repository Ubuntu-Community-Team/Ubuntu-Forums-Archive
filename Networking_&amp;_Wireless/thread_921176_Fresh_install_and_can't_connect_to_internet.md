---
title: "Fresh install and can't connect to internet"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by jjjaroscak on 2008-09-16
**Ok i'm a Linux newb so not sure what if anything I need to do.  I have the following 2 hardware drivers enabled:**
     -Atheros Hardware Acess Layer (HAL)
     -Support for Atheros 802.11 wireless LAN cards.

**This is what I get when I type ifconfig:**
     ```
     eth0      Link encap:Ethernet  HWaddr 00:1e:68:c1:6e:c2  
               UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
               RX packets:58217 errors:0 dropped:0 overruns:0 frame:0
               TX packets:1825 errors:2 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000 
               RX bytes:3848973 (3.6 MB)  TX bytes:250717 (244.8 KB)
               Interrupt:220 Base address:0xe000 

     eth0:avahi Link encap:Ethernet  HWaddr 00:1e:68:c1:6e:c2  
               inet addr:169.254.8.180  Bcast:169.254.255.255  Mask:255.255.0.0
               UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
               Interrupt:220 Base address:0xe000 

     lo        Link encap:Local Loopback  
               inet addr:127.0.0.1  Mask:255.0.0.0
               UP LOOPBACK RUNNING  MTU:16436  Metric:1
               RX packets:1009 errors:0 dropped:0 overruns:0 frame:0
               TX packets:1009 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:0 
               RX bytes:116162 (113.4 KB)  TX bytes:116162 (113.4 KB)
```
     
**and what I type sudo dhclient:**
```
     Internet Systems Consortium DHCP Client V3.0.6
     Copyright 2004-2007 Internet Systems Consortium.
     All rights reserved.
     For info, please visit http://www.isc.org/sw/dhcp/

     Listening on LPF/eth0/00:1e:68:c1:6e:c2
     Sending on   LPF/eth0/00:1e:68:c1:6e:c2
     Sending on   Socket/fallback
     DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
     DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
     DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
     No DHCPOFFERS received.
     No working leases in persistent database - sleeping.

```
[b]Not really sure what to do....  Getting high speed internet from comcast, got a lynksis switch hooked up the the modem....
(Will also be needing help with wireless after I get wired working :-P)[/b]

---

### Post by jjjaroscak on 2008-09-16
bump

---

### Post by jjjaroscak on 2008-09-16
bump again

---

### Post by jjjaroscak on 2008-09-16
Ok weird... I'm at school now and now its working just fine....  So would this be a problem with switch?  Any ideas what's wrong with it and how to fix that?

---

