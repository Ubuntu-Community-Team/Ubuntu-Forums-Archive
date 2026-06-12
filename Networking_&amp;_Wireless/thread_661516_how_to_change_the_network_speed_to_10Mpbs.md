---
title: "how to change the network speed to 10Mpbs"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by backwardbullet on 2008-01-08
The computer that is running Ubuntu is quite a ways from the internet router. Ubuntu can some times connect at 100Mbps but it usually drops the connection in a few seconds I use to have a windows pc at this spot and i changed its settings to 10Mbps. After I did that the connection never dropped out again. But how do I change the settings in Ubuntu? This is the first for me that I have used any other O.S than windows. 




Thanks!:)

---

### Post by Mithrilhall on 2008-01-08
This should get you what you want.

[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

But before dropping your connection to 10Mbps try changing both sides of the connection to 100 Full Duplex if possible.

---

### Post by backwardbullet on 2008-01-08
I whent to applications then to accessories ant to terminal. When I entered the ethtool command this is what I got.

Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000001 (1)
Cannot get link status: Operation not permitted


same with mii-tool

SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted


There are two other computers linked  to the router they both connect at 100mbps F.D

---

### Post by Mithrilhall on 2008-01-08
I believe the ethtool and mii-tool commands are not supported by all cards.

You did run these as 'sudo' correct?

---

### Post by backwardbullet on 2008-01-08
How Do I log on as a Linux sys admin? I have never ever used lunix before now.

---

### Post by backwardbullet on 2008-01-08
Ok that helped! When I put the sudo in front of the command this is what I got


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

---

### Post by backwardbullet on 2008-01-08
Ok I tried it on this computer running ubuntu live cd and it worked! I will go try is on the other system

---

### Post by backwardbullet on 2008-01-08
Got it working! Posting from problem computer
 Thank you!

---

### Post by Mithrilhall on 2008-01-08
Glad I could help.

---

### Post by GlennW on 2008-01-11
Mithrihall, I've been following this and can change settings to what you've suggested after digging back through old posts but I can't keep the settings.

[INDENT]glenn@glenn-desktop:~$ sudo ethtool -s eth0 speed 100 duplex full autoneg off && sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: no
[/INDENT]

I'd like to be able to maintain these settings since it would then be one less thing worry about. I have incredibly slow responses in FF primarily.

Thanks.

---

