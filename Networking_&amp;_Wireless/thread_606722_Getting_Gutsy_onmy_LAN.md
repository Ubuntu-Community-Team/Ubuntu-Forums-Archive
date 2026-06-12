---
title: "Getting Gutsy onmy LAN"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Hansje on 2007-11-08
Hi there,

I have a Dual-boot Win XP with Ubuntu Gutsy Gibbon. My mobo is GA-P35-DS4 witch has a Realtek Ethernet Card onbaord (RTL8111/8168B PCI Express Gigabit Ethernet controller according to the Device Manager of Ubuntu). After a lot of gooling around I disabled ipv6, reinstalled Network Manager, also I followed this tread: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Here is the output of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:47:E8:E6  
          inet addr:192.168.10.229  Bcast:192.168.10.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:22230 (21.7 KB)  TX bytes:11477 (11.2 KB) 
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

```

ethtool eth0:
```
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
```

For me everything is OK... but still, no connection in FF, no connection with Pidgin, no ping possible (Also my router isn't pinging back).
I have an easy questions: 
 -what exactly means 'Bcast:192.168.10.255' ? There is no such an ipadress in my network. 

In the tread about dualboot with windows xp with this network card there where some people who managed to fix this problem by installing an earlier driver in windows XP, but I con't find one older than mine.

Are there other things I can try to fix this?

Greetz

---

### Post by timcredible on 2007-11-08
'Bcast:192.168.10.255'  is the broadcast address of the subnet you're on - don't worry, it's ok.  it's a network thing, not a linux vs. windows thing.

as for it not working, what's not working?  you have an ip address and subnet mask, do you have a default gateway (netstat -r)?  what are you trying to get to?  what's the ip address of your router?  also, why did you mess with the network stuff to begin with?

---

### Post by Hansje on 2007-11-08
Thanks a lot, problem solved because you told me what that broadcast thing is, my router ip was 192.168.10.0, wich is no problem for windows, but it is a broadcast thing in linux (I realy need to do some research about what this broadcast thing is...). So after taking a look at netstat -r I realised what was going wrong...

---

