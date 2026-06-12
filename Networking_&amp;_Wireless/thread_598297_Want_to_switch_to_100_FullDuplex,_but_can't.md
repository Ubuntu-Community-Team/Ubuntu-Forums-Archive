---
title: "Want to switch to 100 FullDuplex, but can't"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Factory on 2007-10-31
Hey guys, having a bit of trouble switching my ethernet connection to 100Tx-FD. I'm at a university, so I have no access directly to the switch that I'm connected to, so I can't give you any specifics on my end. However they have told me that that's the speed they support.

Here's some output for ya'll:

```
rpj8@GettinJiggyWiddit:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```

```
rpj8@GettinJiggyWiddit:~$ mii-diag -A 100
Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported
rpj8@GettinJiggyWiddit:~$ sudo mii-diag -A 100
Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported

```

Any help is appreciated.

---

### Post by Lambert on 2007-10-31
Try this command.

```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```

---

### Post by Factory on 2007-10-31
> **Lambert said:**
> Try this command.

```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```

I will try this when I get a chance. Last time I tried to do this, sudo ethtool eth0 still reported "half" as duplex mode, although I didn't try to turn off auto negotiations.

EDIT:
THANK YOU! This worked!

---

### Post by Factory on 2007-11-08
Ok, new question: How do I automate this? It's kind of a pain to hit this in every time I boot up.

---

### Post by Lambert on 2007-11-09
> **Factory said:**
> Ok, new question: How do I automate this? It's kind of a pain to hit this in every time I boot up.

depending on the device driver, it might be possible to add options when the module loads, would need to know what this is and research more.

An alternate method writing a script can be found here. go down to the debian/ubuntu section. You would need to add a section about turning autoneg off.

[http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html](http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html)

and as a last method, you can edit /etc/network/interfaces and add a line under the eth0 section that says

post-up ethtool eth0 ..........

enter the same command you ran in the past to change settings. you don't need sudo though.

---

