---
title: "Avahi + vmware interfaces"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by neurosis on 2008-02-25
I'm having a bit of trouble with Avahi - excuse me if I'm using the wrong terminology, but it seems to be binding to the wrong interface.

ifconfig shows me lo, eth0, vmnet1 and vmnet8. When started, Avahi binds to one of the vmnet addresses, and when I ping myhost.local it uses the "fake" vmnet ip, instead of my local LAN ip.

I've done alot of searching and can't seem to figure out how to get Avahi to use one specific interface.

Anyone run into this? A temporary fix is to ifdown the vmnet interfaces and restart Avahi, but this isn't a good long term solution.

Help appreciated!

---

### Post by HermanAB on 2008-02-25
Hmm, I always kill the avahi and resolvconf daemons.  They are not worth the trouble.  I just use plain DHCP.  I guess that is not what you wanted to hear, but DHCP is properly configurable.

Cheers,

Herman

---

### Post by neurosis on 2008-02-25
I did figure out a workaround, in case anyone else runs into this. The trick is to disable multicast on the vmnet* interfaces with a command like:

```
ifconfig vmnet1 -multicast
```

avahi-daemon then ignores these interfaces. Seems like a bit of a crazy solution, but this is what the developers have suggested. (Missed this in the Avahi FAQ)

---

