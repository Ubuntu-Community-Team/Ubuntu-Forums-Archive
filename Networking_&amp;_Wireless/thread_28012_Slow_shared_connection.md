---
title: "Slow shared connection"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by man.life on 2005-04-18
I just installed Kubuntu in my sister's laptop (Winblows didn't want to boot). We have a router and until today both PCs could download ~53kb/s at the same time. Now, whenever both computers are connected to the internet, this connection seems to split in two: if she's downloading something at the max. speed, I can't receive anything. But when she's not connected, I get a normal speed.

She's running Kubuntu RC and I'm running Ubuntu 5.04 Final. How can I solve it? I never had this issue with Winblows.

Thanks.  :)

Edit: sorry, this should go into the other networking subforum.

---

### Post by geekgod on 2005-04-18
Try this.....
[http://www.ubuntulinux.org/wiki/WebBrowsingSlowIVP6IVP4](http://www.ubuntulinux.org/wiki/WebBrowsingSlowIVP6IVP4)

also might help is what router are you using

---

### Post by man.life on 2005-04-19
The router is a 3com 812, and it's around 2 years old. But the connection wasn't slow until shared (it's fast when not shared), using Ubuntu and, therefore, IPV6.  :??

---

### Post by geekgod on 2005-04-19
the same issue happens in win32 platforms with aegis.. if the hardware does not support ipv6 then your passing a bunch of unroutible garbage to it and poof slowing it down... the two abuntu systems passing the router what it thinks are malformed packets it may be equal to a DoS attack

---

### Post by man.life on 2005-04-19
Edit: changed /etc/modprobe.d/aliases in both computers and the problem is still there (even after reboot). I've just tested it to be sure:

Laptop downloading something => PC can't even load Google
Laptop in Google homepage / nothing loading => normal speed
Laptop is shut down => normal speed

---

### Post by man.life on 2005-04-20
Could it be related to the fact she's using a release candidate? Should I dist-upgrade?

---

