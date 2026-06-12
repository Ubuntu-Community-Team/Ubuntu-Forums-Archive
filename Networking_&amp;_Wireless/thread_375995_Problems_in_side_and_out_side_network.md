---
title: "Problems in side and out side network"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by CrioStage on 2007-03-04
hi,

idk how to explain this problem ... seens to be an network problem. i have a small network with a router w/ firewall and 5 pcs on it. 1 of them is my server witch i decided to try out ubuntu. i have ssh, samba and a torrent manager torrentflux so i can manage my download over http. recently a wierd problem appeared only in the ubuntu machine. If i ping the machine i get replies of 3000ms or even time out ssh works VERy slow i put the password and user takes me at least 2 min to do it, and the http seens to work abit slower but fine (both out side and inside my network). after i restart the computer all works fine for a couple of days, anyone can help me see whats wrong? 

thx in advance

---

### Post by chili555 on 2007-03-04
Wonder if it's really a network problem or something else.

I suggest that, once you ssh into the under-performer, run top to see if you can see any runaway processes consuming 70-80-90% of your CPU cycles. I might also run sudo tail -f /var/log/messages to see if the kernel is complaining. With some more clues, you, or we may be able to do more.

---

### Post by CrioStage on 2007-03-04
thank you for the fast reply, ext time this happens i will try your recomendations, thank you very much

---

### Post by Mr. C. on 2007-03-04
> **CrioStage said:**
> hi,

idk how to explain this problem ... seens to be an network problem. i have a small network with a router w/ firewall and 5 pcs on it. 1 of them is my server witch i decided to try out ubuntu. i have ssh, samba and a torrent manager torrentflux so i can manage my download over http. recently a wierd problem appeared only in the ubuntu machine. If i ping the machine i get replies of 3000ms or even time out ssh works VERy slow i put the password and user takes me at least 2 min to do it, and the http seens to work abit slower but fine (both out side and inside my network). after i restart the computer all works fine for a couple of days, anyone can help me see whats wrong? 

thx in advance

Top will not solve this prolem.

This is an indication of either a) cable problem, b) switch problem, c) two systems with the same IP, or d) a duplex/speed disparity.

$ ifconfig -a

will give us your network info. 

$ ifconfig -s

will give us some basic ethernet stats

# ethtool -S eth0  # run as root

will give us some NIC statistics.

Run these and show the output.
MrC

---

### Post by CrioStage on 2007-03-05
ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:FF:A3:38
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:feff:a338/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1902415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2072892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1433194978 (1.3 GiB)  TX bytes:1312009557 (1.2 GiB)
          Interrupt:177 Base address:0xa800

eth1      Link encap:Ethernet  HWaddr 00:50:FC:09:11:19
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:334280 (326.4 KiB)  TX bytes:334280 (326.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

ifconfig -s

```
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR   TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0   1902613      0      0      0  2073129      0      0      0 BMRU
lo    16436 0      4477      0      0      0     4477      0      0      0 LRU

```

when i run the last command the output is "no stats available" nothing else =X

but i did the command ethtool  eth0

```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000001 (1)
        Link detected: yes

```

---

### Post by Mr. C. on 2007-03-05
I see no issues on the the eth0 interface.

Perform this again while you are seeing problems, as necessary.  You're looking for errors.  If you have seen the problem prior to your running these commands, it does not appear that this is the system with issues.

I see that your other systems are 192.168.1/24 address w/broadcast:192.168.1.255  and netmask:255.255.255.0.  Have you ensured all the other systems are configured the same, and no IP conflicts?

MrC

---

### Post by CrioStage on 2007-03-05
my router gives the IP by DHCP to other 4 pcs, the ubuntu one i fixed him an IP, because i use FTP/Torrent services so i needed an fixed IP address to foward in the router. Th Ip address given by the router starts in 192.168.1.100 so i fixed the ip address to 192.168.1.10 to avoid conflicts as you can see =X.

To set the Ip address i 1st letted him pick one in automatic dhcp, then took note of the subnetmask checked with windows machines and setup.

---

### Post by Mr. C. on 2007-03-05
> **CrioStage said:**
> my router gives the IP by DHCP to other 4 pcs, the ubuntu one i fixed him an IP, because i use FTP/Torrent services so i needed an fixed IP address to foward in the router. Th Ip address given by the router starts in 192.168.1.100 so i fixed the ip address to 192.168.1.10 to avoid conflicts as you can see =X.

To set the Ip address i 1st letted him pick one in automatic dhcp, then took note of the subnetmask checked with windows machines and setup.

DHCP clients attempt to request the same leased IP they had previous; however, this is not guaranteed.  Should one of your clients end up obtaining the 192.168.1.10 address, there will be a conflict.  It is not safe to use DHCP and a static IP from the same DHCP address pool.

Be sure to limit the routers address pool, and place your static IPs outside that range.

MrC

---

