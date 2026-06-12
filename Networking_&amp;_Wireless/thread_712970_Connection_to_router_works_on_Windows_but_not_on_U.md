---
title: "Connection to router: works on Windows but not on Ubuntu"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by tblom on 2008-03-02
Hello,

I am new to Ubuntu, so please  be patient with me.
I just got a new laptop at work. Both Windows XP and Ubuntu 7.10 are installed on it.
At work I have no trouble connecting to the internet, it works fine on Windows and Ubuntu.

However, now I am trying to get on the internet with this same laptop at home.
When I connect my laptop directly to my cable modem, it works immediately both on Windows and Ubuntu.

The problems arise when I try to connect to my router (Nexland ISB soho). 
My router used to work at 10baseT and 100baseT full-duplex, but a while ago 100baseT all of a sudden stopped working (maybe a defect in my router?), so I always connect to the router at 10baseT full-duplex, with autonegotiation turned off, which works fine.

Using Windows XP, if I set my network card to 10BaseT and turn autonegotation off, I can connect the laptop to the router without problems.

On Ubuntu however, I use the following command:

```
sudo ethtool -s eth0 speed 10 autoneg off
```

which - as far as I know and understand - is the same as what I do on Windows, and I still can't connect to the router.

Afterwards, when I enter the following command:

```
sudo ethtool eth0
```

this is the output I get

```
Supported ports: [ MII ]
Supported link modes:   10baseT/Half 10baseT/Full 
                        100baseT/Half 100baseT/Full 
                        1000baseT/Half 1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes:  Not reported
Advertised auto-negotiation: No
Speed: 10Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: off
Supports Wake-on: g
Wake-on: d
Current message level: 0x000000ff (255)
Link detected: yes
```

I have noticed that when I reset the laptop, the settings are back to 100 Mb/s with autonegotiation turned on. But even after changing the settings and before resetting, I can't make a connection to the router.

Does anyone have an idea what else I could try? Any suggestion would be greatly appreciated!

---

### Post by pdub on 2008-03-02
You can modify your interfaces file:
```

sudo nano /etc/network/interfaces
```

and add this in your adapter section: pre-up /usr/sbin/ethtool -s $IFACE 10 duplex full

```
auto eth0
iface eth0 inet dhcp
**pre-up /usr/sbin/ethtool -s $IFACE speed 10 duplex full autoneg off**
```

---

### Post by tblom on 2008-03-09
OK so I got rid of the router and got a new D-link router combining wireless with wired.
The wired connection works on my laptop without problems now, both on Ubuntu and Windows XP.

But now the problem is the wireless connection. It works on Windows XP but seems very hard to get it working on Ubuntu. 
I am using gutsy, the ipw3945 driver, and WPA-2 personal encryption. 
I can see my wireless network in Network Manager but when I try to connect I don't even get an IP from the router.
However, it has worked 2 times (after waiting for a very long time).
Also, sometimes it asks for my keyring password and sometimes it doesn't.

I read some things about problems with ipw3945 and WPA-2 in gutsy, but haven't found a solution yet that works for me.

Any ideas? Thanks in advance!

---

