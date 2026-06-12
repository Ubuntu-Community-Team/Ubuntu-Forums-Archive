---
title: "Shorewall: ERROR: Invalid Zone Type: Net"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Rhawi Dantas on 2007-02-13
Hi there people... I did the following configuration

[http://deb.riseup.net/networking/firewall/#introduction](http://deb.riseup.net/networking/firewall/#introduction)

Just putting another "net     ppp0" to my interfaces file and I get the error in the title still.
My kernel is a 2.6.17-10-generic with a 3.0.7-1 shorewall version.
And here is my ifconfig result:

eth0      Link encap:Ethernet  HWaddr 00:02:44:8C:64:02  
          inet6 addr: re45::286:4gff:co9z:6402/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:5491715 (5.2 MiB)  TX bytes:1234579 (1.1 MiB)
          Interrupt:58 Base address:0x1100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1364 (1.3 KiB)  TX bytes:1364 (1.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:		  P-t-P:		  Mask:
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5332920 (5.0 MiB)  TX bytes:1083059 (1.0 MiB)

Does someone have a clue ? 

Thanks.

---

### Post by Rhawi Dantas on 2007-02-15
so, is there someone to gimme a hint ?

---

