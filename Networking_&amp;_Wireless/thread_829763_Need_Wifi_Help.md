---
title: "Need Wifi Help"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by kenbuntu09 on 2008-06-15
I've read many posting online and I'm still confused as ever, I suppose I need a new driver but no luck I've download madwifi no idea how to run it or open it, all I simply want to do is use my wifi router, I have it running on windows vista would love to use it on ubuntu need help asap as i've spend 4 hours how to try to figure the damn thing out. help greatly appreciated very much


right now i'm connected to the internet using the router using a RJ45 thats connect to my D-Link Wireless Router unforunetly I cannot get any wireless connections to appear in my network manager, the D-Link Model is DSL-2640T yes it is ethernet cable. When I put iwconfig in terminal this is what came up 
lo        no wireless extensions.

eth0      no wireless extensions

and on command ifconfig this is what came up
eth0      Link encap:Ethernet  HWaddr 00:1a:80:7f:56:28  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:80ff:fe7f:5628/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18189742 (17.3 MB)  TX bytes:1120941 (1.0 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46284 (45.1 KB)  TX bytes:46284 (45.1 KB)
mind you I am currently using this router with a ethernet cable right now but want to use wifi instead

---

### Post by powerpleb on 2008-06-15
It's a router yea, so how do you connect to it, ethernet or usb?

---

### Post by lisati on 2008-06-15
EDIT: Which connection you use depends on the kind of router: ethernet is often better than usb. Once you have connected it, try the following:


There is some information that might help the forum members guide you through getting things going.

For example, you could post the output of ```
iwconfig
```and ```
ifconfig
```

EDIT #2: What model router is it?

---

