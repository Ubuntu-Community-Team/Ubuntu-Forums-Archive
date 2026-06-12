---
title: "Help with internet connection"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by maco101 on 2008-01-19
Hi

I've got a Marvell Yukon 88E8039 natwork card for some reason i cannto go on the net, live done a few thing and it looks like the sky2 driver is installed 

borche@borche-laptop:~$ ethtool -i eth0

driver: sky2
version: 1.18
firmware-version: N/A
bus-info: 0000:02:00.0


and i can see that there is a connection, the problem is when i use the browser, messenger service, or try to update nothing happens.

borche@borche-laptop:~$ sudo ethtool eth0
[sudo] password for borche
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes


borche@borche-laptop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:d1:75:b2:da
Sending on   LPF/eth0/00:a0:d1:75:b2:da
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.3 -- renewal in 1584 seconds.

ive also tried to ping different sites and other pc's in my network and the ping work well.

---

### Post by A4006 on 2008-01-19
I had a similar problem with my wireless card (BTW are you using Wireless LAN or Ethernet?) being able to ping sites on the internet but not being able to browse.  I think it has something to do with the network key.  That was only under Ubuntu 7.04, because I use a WPA-PSK and it did not support that, only WEP.  7.10 cleared that all up.  Try experimenting around with the network keys (assuming you use one).

---

### Post by maco101 on 2008-01-19
its just a normal ethernet connection and the network card is eth0

---

