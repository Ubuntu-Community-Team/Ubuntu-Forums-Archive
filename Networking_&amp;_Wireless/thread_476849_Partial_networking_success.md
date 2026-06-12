---
title: "Partial networking success"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Toolsmith on 2007-06-17
Hi, just installed 7.04 off the live cd to my emachines laptop (I'll call it UB).  Plugged into a switch alongside my Windows machine (Win) which has network connectivity (using it to post this).  UB can ping Win (and Win can ping UB) but UB can't ping the upstream access point or the router.  I read a few posts about network problems so am appending some console listings.  Any suggestions much appreciated - Peter
-------------------
pbuck@pbuck-Ubuntu1:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:03:25:13:71:A7  
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe13:71a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:509025 (497.0 KiB)  TX bytes:8258 (8.0 KiB)
          Interrupt:18 Base address:0x1800 

pbuck@pbuck-Ubuntu1:~$ sudo ethtool eth0
Password:
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
pbuck@pbuck-Ubuntu1:~$ ping 192.168.0.111
PING 192.168.0.111 (192.168.0.111) 56(84) bytes of data.
64 bytes from 192.168.0.111: icmp_seq=1 ttl=128 time=0.686 ms
64 bytes from 192.168.0.111: icmp_seq=2 ttl=128 time=0.178 ms
64 bytes from 192.168.0.111: icmp_seq=3 ttl=128 time=0.175 ms
64 bytes from 192.168.0.111: icmp_seq=4 ttl=128 time=0.181 ms

--- 192.168.0.111 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 0.175/0.305/0.686/0.219 ms
pbuck@pbuck-Ubuntu1:~$ ping 192.168.0.50
PING 192.168.0.50 (192.168.0.50) 56(84) bytes of data.
From 192.168.0.121 icmp_seq=1 Destination Host Unreachable
From 192.168.0.121 icmp_seq=2 Destination Host Unreachable
From 192.168.0.121 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.50 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3009ms
, pipe 3
pbuck@pbuck-Ubuntu1:~$

---

### Post by mitch.c on 2007-06-18
If this is in fact a 'switch' you are connected to, I would be checking it's configuration.

---

### Post by Toolsmith on 2007-06-19
Thanks for the response, Mitch.  I did swap the cables between Win and UB.  Win gets to the Internet on both cables; UB can't on either.  So I thought that eliminated cable and switch port.

However - it has something to do with the configuration at home, because I brought the laptop to work and its networking works as desired (using DHCP, rather than manual configuration).

I'll go back home and do some more experimentation, now that I know that things work somewhere.  If I still have trouble I'll start a new thread.  Thanks again - Peter

---

