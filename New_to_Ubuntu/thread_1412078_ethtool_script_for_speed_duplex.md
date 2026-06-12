---
title: "ethtool script for speed duplex"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by ak07 on 2010-02-20
Hi,

I hope someone can help, I've been researching how to set the speed and duplex settings permanent on the nics in my PC.

I have found this script which uses ethtool

#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
SPEED="100 duplex full"
case "$1" in
   start)
    echo -n "Setting eth0 speed 100 duplex full...";
    $ETHTOOL -s $DEV speed $SPEED;
    echo " done.";;
   stop)
    ;;
esac
exit 0

I have two questions regarding this

[LIST=1]
[*]Is this the best method of permently setting speed and duplex settings?
[*]Using the script above if i wanted to set the settings for more than one nic, for example eth2, eth3 and so on how could I do this using this script?
[/LIST]
Cheers
AK

---

### Post by ak07 on 2010-02-20
Because I am

---

### Post by overdrank on 2010-02-20
Ok back on topic :)

---

