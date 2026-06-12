---
title: "pppd ip-up.d script not executing"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by tomroffe on 2007-05-21
Hi All

Can anyone shine some light on this problem I'm having! I'm currently running a speedtouch 330 ADSL modem on Ubuntu Server 7.04. I can connect and get a working connection and manually run my iptables script but i can not get ppp to run my script located in 

/etc/ppp/ip-up.d/

i have set the file permission of this script to 700 and is owned by root. the script that runs is simple and like say can be run manually from the command line.

```

#!/bin/sh

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables-restore < /etc/network/iptables.up.rules

```

Aim i missing something hear.  The man pages say this is the right place, and i think the other scripts in the ip-up.d directory are being executed, namely 0000usepeerdns  0dns-up or i would not get my peer dns server addresses placed into resolv.conf.

Can anyone help

Thanks Tom

---

