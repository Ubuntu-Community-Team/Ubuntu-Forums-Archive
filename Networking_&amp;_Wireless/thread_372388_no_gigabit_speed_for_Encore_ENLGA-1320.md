---
title: "no gigabit speed for Encore ENLGA-1320?"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by scottbakertemp on 2007-02-28
I just purchased this gigabit card:
[http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=82_8&pid=1]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=82_8&pid=1")
It works out of the box in ubuntu edgy but the speed is only 100 Mbps.  Can anyone tell me how to run the thing in 1000 Mbps?  Can I use the Linux drivers on the company website?  If so how do I install them in Edgy?

thanks in advance

---

### Post by scottbakertemp on 2007-02-28
Here is some more info:
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:54:46:50:AA  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe46:50aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13541 errors:0 dropped:32 overruns:0 frame:0
          TX packets:14535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:860304 (840.1 KiB)  TX bytes:10607941 (10.1 MiB)
          Interrupt:201 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5316 (5.1 KiB)  TX bytes:5316 (5.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ubuntu@ubuntu:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

---

### Post by scottbakertemp on 2007-02-28
anyone?

---

### Post by ScArcher2 on 2007-07-15
I'm having the same problem. I bought two of these cards and put them in 2 Ubuntu machines.
The switch is detecting them as gigabit, but they are only getting about 3-5 megabytes per second transfer times.

---

### Post by gangolli on 2007-07-22
I think this card gets the Realtek RTL8169 drivers by default.  Several people have reported  similar issues.
This thread suggests you blacklist it and take the r1000 instead.

[http://ubuntuforums.org/showthread.php?t=143982](http://ubuntuforums.org/showthread.php?t=143982)

---

