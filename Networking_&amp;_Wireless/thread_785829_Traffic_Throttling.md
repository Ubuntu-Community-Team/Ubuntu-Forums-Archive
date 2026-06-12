---
title: "Traffic Throttling"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by linuxwarz on 2008-05-07
I am using Ubuntu 8.04 as a router with iptables.

I would like to throttle WAN speeds per computer so no one person can use up all of the bandwidth.

Does anybody have a favorite script or know some commands that might direct me in the right direction?

For sake of example, lets say my connection is 12000/1500kbit

---

### Post by Boozkachu on 2008-12-17
Hi,

Probably the best way would be to check if your router has QoS settings to allow some traffic shaping, otherwise perhaps look at using an alternative firmware for it.

Cheers.

---

### Post by Boozkachu on 2008-12-17
Oops I see you are using the computer as a router :)
Well you could try:
[http://www.mastershaper.org]("http://www.mastershaper.org")
or
[http://lartc.org/]("http://lartc.org/")

;)

---

### Post by iponeverything on 2008-12-17
check out this thread for a good example of how to do it.

[http://ubuntuforums.org/showthread.php?t=946624](http://ubuntuforums.org/showthread.php?t=946624)

---

