---
title: "problem aliasing &gt; 2 ip addr to eth0"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by RoyB (Aus) on 2006-08-25
in /etc/networks/interfaces I've specified a port, eth0 and two alias addresses.  (file content below).

The system will bring up only the first of the aliases, not both of them.  If I manually enter ifconfig eth0:2 192.168.1.200 etc that works.  But if I put the same statement into /etc/rc.local it doesn't work.  

Can anyone suggest what I can look at to remedy?

/etc/networks/interfaces :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address         192.168.1.8
        netmask         255.255.255.0
        network         192.168.1.0
        broadcast       192.168.1.255
        gateway         192.168.1.1
        mtu             1492

auto eth0:1
iface eth0:1 inet static
        address         192.168.1.202
        netmask         255.255.255.0

auto eth0:2
iface etho:2 inet static
        address         192.168.1.200
        netmask         255.255.255.0

---

### Post by spd106 on 2006-08-25
Did you copy and paste this from the config file?

Spot the mistake.

> auto eth0:2
iface etho:2 inet static
address 192.168.1.200
netmask 255.255.255.0


Yes, on the second line you have an o instead of a 0.

---

### Post by RoyB (Aus) on 2006-08-29
Amazing how I stared at it for hours and didn't see it and you stared at it for (I assume) seconds and saw it.

Thanks!

---

### Post by spd106 on 2006-08-29
You wouldn't believe how many times I've made that mistake. Usually do it directly with ifconfig and get an error.

I really should learn how to touch type.

---

