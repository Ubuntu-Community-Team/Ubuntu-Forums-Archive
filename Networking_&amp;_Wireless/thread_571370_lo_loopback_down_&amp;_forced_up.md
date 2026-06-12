---
title: "lo loopback down &amp; forced up"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by justin4dti on 2007-10-09
I switched a ubuntu box from dynamic to static and now it's loopback will only come up by root/wheel user logging in and forcing it down and then up.  Yes,* down then up*; $ifup claims that lo is already up even though $ifconfig only lists eth0.  I tried hacking this peculiar sequence of ifdown and ifup in /etc/rc.local but even it doesn't automatically bring lo up. 

And yes, I realize Ubuntu does this from /etc/rcS.d but obviously that's not working.  There is a [similar thread]("http://ubuntuforums.org/showthread.php?t=80454") that was not resolved.  All similar threads worry about /etc/networking/interfaces, so here's the loopback part:

```
auto lo eth0
iface lo inet loopback
...

```

The only thing I haven't tried is explicitly setting the address and netmask for loopback in /etc/networking/interfaces (because I haven't seen that as a consistent config for Ubuntu ... I'm more a CentOS and Gentoo guy ;)

---

### Post by noob12 on 2007-10-09
You can't combine the auto for lo and eth0.  Take the eth0 off the auto lo line.

If you want an auto for eth0 put it on a separate line.

Cheers.

---

### Post by justin4dti on 2007-10-09
eh??  manpage interfaces (5):

> 
Here is an example.

auto lo eth0
...


Although, being a good lil penguin, I had already tested separate auto lines. ;)

---

### Post by noob12 on 2007-10-09
Yep, sorry.  Hadn't noticed that in the man page.

After you boot what does **cat /var/run/network/ifstate** say ?

---

