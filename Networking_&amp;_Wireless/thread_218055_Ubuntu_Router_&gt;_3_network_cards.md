---
title: "Ubuntu Router &gt; 3 network cards"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by antilog on 2006-07-18
Background:
eth0 - cable modem
eth2 - internal network (a switch)
ath0 - wifi, in AP mode
using Firestarter

eth2 is serving DHCP well, and my laptop sees ath0 AP, but does not get an IP from it.  first of all, can both eth2 and ath0 be on the same subnet ex: 192.168.0.x?  I am not sure how to configre the dhcpd.conf file for this, and I am not sure how Firestarter will handle it since its GUI only gives a choice for one internal network card.

any ideas?  you all have been so helpful, thanks.

---

### Post by mips on 2006-07-18
Have a look at the link below, might have to adapt a bit to your situation.

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by antilog on 2006-07-23
Thanks for the link, I looked over that quite a bit.  It seems to connect, but will not serve an IP.  I am guessing this is a DHCP configuration.

I ended up using a wifi router as an AP, which is getting away from the goal of this project...

Thanks

---

