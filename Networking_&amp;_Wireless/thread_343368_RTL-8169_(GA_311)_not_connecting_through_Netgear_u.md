---
title: "RTL-8169 (GA 311) not connecting through Netgear unmanaged switch"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by silverado on 2007-01-21
Problem Summary: Ubuntu 6.10 desktop will not connect to network through netgear GS605 v2 unmanaged switch.  

Network configuration:

WNR854T --> (1) Windows XP & (2) Wireless Computers & (3) GS605 --> (1) [COLOR="Red"]Ubuntu w/ GA311[/COLOR] & (2) Windows XP w/ GA311

ethtool dump when connected to GS605 _AND_ nothing at all:

thor@ValHalla:~$ sudo ethtool eth0
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
        Speed: **[COLOR="Red"]100Mb/s[/COLOR]**
        Duplex: **[COLOR="Red"]Half[/COLOR]**
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no

Troubleshooting steps applied:

(1) Direct connected to Netgear Router WNR854T and ran ethtool with following dump:
thor@ValHalla:~$ sudo ethtool eth0
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
        Speed: **[COLOR="Red"]1000Mb/s[/COLOR]**
        Duplex: **[COLOR="Red"]Full[/COLOR]**
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: **on**
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: **yes**

It works =D> !!! But... When I connect back through the switch and run some more tools:

(2) Ran sudo ethtool -s eth0 autoneg off speed 1000 duplex full w/ **no effect.** ](*,) 
(3) shutdown network connection with sudo ifdown eth0 and ran ethtool w/ **no effect**. ](*,) 
(4) created script file in /etc/network/if-pre-up.d to turn off auto negotiation w/ **no effect**. ](*,) 

So I am still at the point where I can connect directly through the router but not through the switch.  I read something about a 3com adapter that requires firmware changes to make it not use the "most compatible" mode when not directed to use the "highest performance"

Thanks for any advice in advance

---

