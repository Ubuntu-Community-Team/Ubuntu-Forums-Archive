---
title: "Atheros interface does not start at boot."
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Misha__ on 2008-07-06
Quite strange problem. 
I have the following /etc/network/interfaces:
```
auto lo
iface lo inet loopback

iface eth0 inet static
address xx.xx.xx.xx
netmask xx.xx.xx.xx
gateway xx.xx.xx.xx
auto eth0

iface ath0 inet static
madwifi-base wifi0
madwifi-mode master
wireless-essid essid
address 192.168.1.2
netmask 255.255.255.0 
pre-up iptables-restore < /etc/iptables.conf
auto ath0
```
After reboot there is no ath0 interface. 
When I am trying to start it with ifup, it complains with something like "interface is already configured". Still, after ifdown/ifup it shows up and works well. 
```

$sudo ifup ath0
ifup: interface ath0 already configured
$ sudo ifdown ath0
ath0: ERROR while getting interface flags: No such device
$ sudo ifup ath0

```

I have Ubuntu 8.04.1.
Did anyone see this problem and/or solution?
Thanks in advance.

---

### Post by hcgpragt on 2008-11-02
Hi,
came across your post. 
I found the solution here: [http://ph.ubuntuforums.com/showthread.php?t=731361&page=2](http://ph.ubuntuforums.com/showthread.php?t=731361&page=2)

Cheers,

H
:popcorn:

---

