---
title: "Ethernet Problems with Gutsy"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Harlon Nayl on 2008-02-18
I installed Gutsy in mid-January. At the time, I was able to use my ethernet port (in roaming mode, through a router) to download ndiswrapper and set up my wireless card. After going back to school, I was unable to get a connection from either wired or wireless connections. To make matters worse, now neither device works at home, where they were originally configured. Right now, I'm only concerned about getting the wired connection working, I'll deal with the wireless later. My ethernet device is a Realtek RTL8139, and the mod command shows that the 8139too driver is loaded. Here's the output from several terminal commands:

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

Note: I've tried manually adding entries for eth0 (the wired device), but no luck. Given that eth0 isn't listed in the interface file, ifup and ifdown commands don't work.

route -n produces blank output

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:3E:AD:68  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:124 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:BE:EE:96  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)


$ sudo ethtool eth0
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
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```

As a final note, I'm unable to ping any IP address, including my router. The ping command produces a "network is unreachable" error. Also, I have tried setting up both dhcp and static connections. Any help would be appreciated.

---

