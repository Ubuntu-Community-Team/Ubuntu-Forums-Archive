---
title: "Changing speed duplex settings permanently."
date: 2011-07-21
forum: New to Ubuntu
---

### Post by openlions on 2011-07-21
Just switched to Ubuntu 11o4 yesterday and i'm lovin it...
But needed a little help about changing speed duplex settings permanently.
I use the 'sudo ethtool -s eth0 autoneg off speed 10 duplex half' command but it doesn't last a reboot.
Anybody knows how to make this change permanent?
I tried adding the 'pre-up /usr/sbin/ethtool -s $IFACE autoneg off 10 duplex half' line to /etc/network/interfaces but then the internet just doesn't work.
What should I do to permanently change speed and duplex settings to 10Mbps half duplex? (I'm just a beginner so please explain step by step)
Just for info- The contents of the /etc/network/interfaces file are as follows-
auto lo
iface lo inet loopback

---

### Post by jtarin on 2011-07-21
> **openlions said:**
> Just switched to Ubuntu 11o4 yesterday and i'm lovin it...
But needed a little help about changing speed duplex settings permanently.
I use the 'sudo ethtool -s eth0 autoneg off speed 10 duplex half' command but it doesn't last a reboot.
Anybody knows how to make this change permanent?
I tried adding the 'pre-up /usr/sbin/ethtool -s $IFACE autoneg off 10 duplex half' line to /etc/network/interfaces but then the internet just doesn't work.
What should I do to permanently change speed and duplex settings to 10Mbps half duplex? (I'm just a beginner so please explain step by step)
Just for info- The contents of the /etc/network/interfaces file are as follows-
auto lo
iface lo inet loopbackHere's the [recipe]("http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/").....note the[ links]("http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html") at the bottom of the article about making it permanent.

---

