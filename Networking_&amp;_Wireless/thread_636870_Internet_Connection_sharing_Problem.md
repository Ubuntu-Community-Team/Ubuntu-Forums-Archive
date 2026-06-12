---
title: "Internet Connection sharing Problem"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by anzen on 2007-12-10
Ok, i want to share my ubuntu box's internet connection with an winXP box through a crossover cable.

So far, i've tried to use Firestarter. 
I set eth1 as the "internet connected network device"
and eth0 as the "local network device"

and..... no luck. if i turn on the firewall, ubuntu can't connect to the internet.
winXP also cannot connect.

And i've also tried all the instructions and comments at these pages:

[http://ubuntuforums.org/showthread.php?t=83428](http://ubuntuforums.org/showthread.php?t=83428)
[http://ubuntuforums.org/showthread.php?t=604104](http://ubuntuforums.org/showthread.php?t=604104)
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)


Here are the current settings i currently use in which:

- I can access the internet with ubuntu 
- winXP cannot access the internet 
- I can also see the shared files on each computer with no problems
- They can ping each other as well

They are connected in this manner:
```
[DSL modem](192.168.1.1) --> (eth1 192.168.1.3)][Ubuntu](eth0 192.168.0.1) --> [Windows(192.168.0.5)]
```

```
------------------------------------------
[DSL modem]
 - Connected to to Ubuntu's eth1
 - IP: 192.168.1.1
------------------------------------------
[UBUNTU]
eth1  
 - connected to the DSL modem
 - IP: 192.168.1.2 subnet: 255.255.255.0

eth0
 - connected to the NIC of the winblows machine
 - IP: 192.168.0.1 subnet: 255.255.255.0
------------------------------------------
[Windows]
 - Has only 1 NIC
 - Connected to Ubuntu's eth0
 - IP: 192.168.0.5 subnet: 255.255.255.0
 - DNS: 192.168.0.1
 - Gateway: 192.168.0.1
------------------------------------------
```

also here's my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:A1:B0:F1:5D:9E  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5924 (5.7 KB)  TX bytes:3480 (3.3 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:19:21:44:00:25  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91743 (89.5 KB)  TX bytes:65555 (64.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:58.69.183.204  P-t-P:210.213.218.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:73154 (71.4 KB)  TX bytes:44096 (43.0 KB)
```

routes:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
210.213.218.254 *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0

```

Hope someone can help me :)

---

### Post by fineas on 2007-12-10
Does this works for you? [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

---

### Post by anzen on 2007-12-10
no it doesn't sorry... i've already tried that one too.

EDIT:
should i use eth1 or ppp0 on firestarter's "internet connected network device"

---

### Post by anzen on 2007-12-11
BUMP...

No one knows?

hmm i'm trying to share it my internet connection but i still have no luck at all...

---

### Post by anzen on 2007-12-18
BUMP....

Still no luck here... any ideas?

---

### Post by meeces2911 on 2007-12-22
anyone got any ideas ?? ive tried firestarter and the ubuntugeek thing ...:confused:
Im trying to set up a thin server network, and i really need to share the internet connection.


Oh and just incase anyone was wondering ... my set up is something like this ->

Internet ->eth0 - Ubuntu 7.1 Server (Thin-Server using ltsp)
from there it goes to 2 different thin clients through eth1 and eth2
so, yes.. i have 3 different nic on the server.
DHCP is running from the ubuntu server on both eth1 and eth2
and eth0 is getting dhcp from the modem.

So yea, i really need the internet connection sharing thing!!

---

### Post by diazjavier on 2007-12-28
> So far, i've tried to use Firestarter. 
I set eth1 as the "internet connected network device"
and eth0 as the "local network device"

I have the same configuration. I made it work (internet connection with Firestarter on) setting "ppp0" as the "internet connected network device" (insteed "eth1") ... but no sharing internet connection with the other machine.
Sorry for my english.

---

