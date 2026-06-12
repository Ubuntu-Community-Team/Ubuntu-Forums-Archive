---
title: "force duplex to full?"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by veritas366 on 2005-05-07
Okay, let me try this way.  Somebody not from this forum suggested I needed to switch duplex to full.  I went to my ethtool and saw that, indeed, it was at half.  I don't know what this means, exactly, but I found the command to switch it to full.  However, it didn't seem to do anything.  Here is my ethtool readout, my issuing the command and the readout afterward.  What else do I need to do?

By the way, the point of this is that my Ubuntu cable modem connection is about half the speed as when I use Windows on the same box.  

> settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes
ty@ubuntu:~ $ sudo ethtool -s eth0 speed 100 duplex full
ty@ubuntu:~ $ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/ss
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes


Any help would be appreciated.

---

### Post by ubuntu_demon on 2005-05-09
[QUOTE=veritas366]Okay, let me try this way.  Somebody not from this forum suggested I needed to switch duplex to full.  I went to my ethtool and saw that, indeed, it was at half.  I don't know what this means, exactly, but I found the command to switch it to full.  However, it didn't seem to do anything.  Here is my ethtool readout, my issuing the command and the readout afterward.  What else do I need to do?

By the way, the point of this is that my Ubuntu cable modem connection is about half the speed as when I use Windows on the same box.  



Any help would be appreciated.[/QUOTE]
 10 mbit = max speed is 10 mbit
100 mbit = max speed is 100 mbit
half duplex = only one of the two network devices can send at the same time
full duplex = both can send at the same time

100 mbit full duplex is obviously the best setting. In most cases auto negotiation works fine and gets the best setting, In some rare cases you have to revert to configuring your network card by hand.

First you should look up the capabilities of both network devices (the network device in your pc and the one at other end of the line for example your cable modem). You don't have to try modes that aren't supported at all.

You should try setting it by hand using ethtool (see man ethtool for more on this) in this sequence (except from the modes that aren't supported at all:

100 mbit full
100 mbit half
10 mbit full
10 mbit half

you shouldn't touch the other settings of your network card.

---

### Post by doc_holiday on 2005-07-11
How can I  check my link speed/duplex?

---

### Post by ubuntu_demon on 2005-07-11
[QUOTE=doc_holiday]How can I  check my link speed/duplex?[/QUOTE]
 $ sudo ethtool eth0
if your device is named eth0

---

### Post by doc_holiday on 2005-07-11
[QUOTE=ubuntu_demon]$ sudo ethtool eth0
if your device is named eth0[/QUOTE]

Thanks, I should have read the top post twice.

---

