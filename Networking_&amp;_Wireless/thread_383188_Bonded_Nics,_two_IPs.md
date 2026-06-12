---
title: "Bonded Nics, two IPs"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by lyna on 2007-03-13
Hi all,

I've used ifenslave to bond my two NICs to a round-robin/failover type of
interface.  It seems to work well enough, so now, naturally enough, I want
to change it.

I'd like to have two IP addresses accessible via the bonded interface, just as
I was able to when using only one NIC (/etc/network/interfaces entry for
eth0:1).  Could I do something similar, e.g.

   iface bond0:1 inet static
    address  xxxxxx
    netmask xxxxx
...etc

Or would this be pushing the friendship too far?

Cheers,
Lyn

---

### Post by Mr. C. on 2007-03-13
You mean create an alias IP.  I believe you should be able to do this.

MrC

---

