---
title: "Wake on Lan help configure"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by KindredCharles on 2008-08-28
Trying to set up wake on lan, I turned it on in the bios and on my interface. I used wakeonlan to send the packets to the computer and I could see the nic activity led blinking when I did.

```
sudo ethtool eth0
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
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:87:e0:90
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe87:e090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:56913670 (54.2 MB)  TX bytes:540977 (528.2 KB)
          Base address:0xc000 Memory:f2000000-f2020000

```


I didn't think there were any more steps, anyone wanna point out what i'm missing? Thanks!

---

### Post by KindredCharles on 2008-08-28
My mistake this was not a problem with my set-up for the linux wol, it was a problem over wan. I need to figure out how to forword packets to a broadcast address from the internet with my router. on linksys site now,

I also added the changes mentioned in the last post here
[http://ubuntuforums.org/archive/index.php/t-602520.html](http://ubuntuforums.org/archive/index.php/t-602520.html)

---

