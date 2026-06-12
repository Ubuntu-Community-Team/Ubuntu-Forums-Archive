---
title: "Linux-Windows LAN"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by zadirion on 2007-10-16
I am trying to share my internet connection on a Ubuntu(Gusty Gibbon) box with a Windows XP Laptop. Currently I can't even ping the laptop let alone share internet connection.
This is my ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:14:D1:32:20:FA  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe32:20fa/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69946 (68.3 KB)  TX bytes:11349 (11.0 KB)
          Interrupt:16 Base address:0xa400 

eth1      Link encap:Ethernet  HWaddr 00:13:8F:36:F2:6B  
          inet addr:192.168.44.0  Bcast:192.168.47.255  Mask:255.255.240.0
          inet6 addr: fe80::213:8fff:fe36:f26b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:425382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322592062 (307.6 MB)  TX bytes:13195457 (12.5 MB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119050 (116.2 KB)  TX bytes:119050 (116.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:86.126.88.229  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3510454 (3.3 MB)  TX bytes:448988 (438.4 KB)


where eth0 is my LAN network adapter, and eth1 my internet connection.
I connect the computers directly with a crossover cable. What do I need to do?
As i told you, I can't even ping the laptop, or viceversa(Firewall on laptop is disabled)

---

### Post by dmizer on 2007-10-16
well, start with disabling ipv6:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

then you'll need to set up nat for your 194.168.44 subnet:
[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

ideally, you should have a router for pppoe authentication so you don't have to muck with internet connection sharing and software firewalls, but in a pinch the above will suffice.

humm ... as for the ping issue, your windows and your 194.168.44 subnet are set up with static ip and no gateway address?

---

### Post by mocoloco on 2007-10-16
I recall reading in Tux Magazine that firestarter (the firewall app) makes setting up ICS easy, though I've never done it myself.

---

### Post by Synflux on 2007-10-16
Hello,

Some of this doesn't sound quite right?
> where eth0 is my LAN network adapter, and eth1 my internet connection.
Is eth1 really the internet connection? It has a private address and a /20 subnet mask which seems very generous of your ISP?!  I think maybe that ppp0 is your internet connection which has a single public IP?

Are you plugging your laptop into eth0 or eth1? What is your laptop's IP when it is plugged in? Please post "ipconfig /all" output from your laptop (without speech marks).

As mocoloco says Firestarter has an option that will allow you to share your ppp0 connection through one of your ethernet connections.

Hope this helps you.

:)

---

### Post by zadirion on 2007-10-17
Well I solved the ping problem by setting static IPs instead of using DHCP.
The device I use for internet is eth1 although the connection is ppp1. I use optic fiber and use a username and pass to connect to the internet so that may explain a few things(or not).
File sharing works between the PC and the laptop.
I use firestarter, and set the lan to ppp0, I have the rules set, so that problem is excluded.
Just to be on the safe side, firestarter GUI is opened and filtering is stopped. LAN cable is plugged into the eth0 device.

---

