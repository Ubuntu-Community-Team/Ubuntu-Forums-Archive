---
title: "Check ethernet"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by slink on 2007-10-15
Hi, 

I suddenly lost my Internet connection during a lightning storm. 2 days later my DSL router blinks again but I still have no Internet. 

My provider says I need to check if the computer recognizes my network card. So I've done:

> [FONT="Courier New"]felix@ordinador:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr  
     UP BROADCAST MULTICAST  MTU:1500  Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000 
     RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
     Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr 
     inet addr:***.***.9.22  Bcast:***.***.255.255  Mask:255.255.0.0
     UP BROADCAST MULTICAST  MTU:1500  Metric:1
     Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
     inet addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:50 errors:0 dropped:0 overruns:0 frame:0
     TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0 
     RX bytes:3688 (3.6 KiB)  TX bytes:3688 (3.6 KiB)[/FONT]

Yes, I've censored my IP adress...

I've also done:

> [FONT="Courier New"]felix@ordinador:~$ lspci | grep Ethernet
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)[/FONT]

Can I assume that my system recognizes my ethernet card, and that it has a valid IP adress ?



When I try to ping the router:

> [FONT="Courier New"]felix@ordinador:~$ ping ***.***.9.1
PING ***.***.9.1 (***.***.9.1) 56(84) bytes of data.
From ***.***.9.22 icmp_seq=2 Destination Host Unreachable[/FONT]

I also tried:

> [FONT="Courier New"]felix@ordinador:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
felix@ordinador:~$ sudo mii-diag
Password:
Using the default interface 'eth0'.
Basic registers of MII PHY #1:  3000 7849 0000 8201 01e1 0000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x7849 ... 7849.
   Link status: not established.
   End of basic transceiver information.

felix@ordinador:~$ sudo mii-tool
eth0: no link[/FONT]

Can anyone help me diagnose my "problem" ?

---

### Post by Jussi Kukkonen on 2007-10-15
> Yes, I've censored my IP adress...
You said your behind a router so I don't think that's necessary.
> Can I assume that my system recognizes my ethernet card,

Yes, although there's no proof it's working correctly (I'd assume so though).
> 
... and that it has a valid IP adress ?
No. Zero packets hace been sent/received. I'm guessing your card works, but the router doesn't (you could try this with second router or computer to be sure).

---

### Post by slink on 2007-10-15
> you could try this with second router or computer to be sure


do you refer pinging 127.0.0.1 ?


I had 2 PC's+router ago, but now it's 1 PC+ROUTER

---

### Post by Jussi Kukkonen on 2007-10-15
Just meant that if you had another computer you could test the router with the other computer, and if you had another router you could test the computer with that (if the computer is portable, this should be easy).

---

