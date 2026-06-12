---
title: "Network disconnect slows down computer"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by amenon on 2007-03-12
When I setup my network (either wired or wireless) and go away from that network (disconnect the ethernet cable, or go out of range of the wireless network), the computer slows down.

It looks like some program is trying to look for the DNS servers. Once I empty the resolv.conf file, the computer is back to normal.

Does anybody have any idea why this could be happening?

---

### Post by Mr. C. on 2007-03-12
Almost all network-enabled programs require name services to translate hostnames into IP addresses and perform other lookups.

I have no idea in your case what programs are attempting DNS lookups.  There are several desktop apps that do.

If you disconnect from the network, bring down the interface, as in :

```
ifdown eth0
```
MrC

---

### Post by amenon on 2007-03-12
Yeah I do bring down my network and bring it back up once I am connected. But if I forget to do this, then even opening up a terminal to bring down the network takes about 5 minutes.

Oh well, I guess, I'll keep looking.

---

### Post by Mr. C. on 2007-03-12
If I forget to put gas in my car, I have to walk. :-)

Basically, network apps need to perform looks.  The lowest layer that performs these for all apps is the libc resolver.  There is a 15 second timeout before additional servers are tried or the service gives up.  Basically, there is no way to differentiate between a slow response and no response, other than to wait a predetermined time.

MrC

---

