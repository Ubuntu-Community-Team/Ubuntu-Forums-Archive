---
title: "Removing route - no internet"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2007-05-26
Hi there,

screwing around tonight I entered the command dhclient.

after that, even after restart my internet connection has been dodgey. Gaim works, but firefox doesn't. I went trouble shooting and found a new entry in my routeing list. 
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
192.168.14.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.126.0   *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
[COLOR="Red"]default         192.168.14.2    0.0.0.0         UG    0      0        0 vmnet8[/COLOR]

How can I remove this entry?

thanks,

rudolf

---

### Post by spd106 on 2007-05-26
Try ```
sudo ip route del default via 192.168.14.2 dev vmnet8
``` if that doesn't work then try ```
sudo /etc/init.d/networking restart
```

---

