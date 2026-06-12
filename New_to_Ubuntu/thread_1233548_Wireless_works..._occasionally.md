---
title: "Wireless works... occasionally"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by payko526 on 2009-08-06
I installed 9.04 on an old laptop of mine, and I linked it to my wireless (N) network.  It works some days, but others it gets stuck in a loop where it asks me for the password to my (WPA-TKIP) secured router.  I'm not sure what's happening, because I still get sporadic incidents where it works perfectly, but other days it just loops.

More info, in case I've left anything out:
Wireless-G card
Intel Celeron-M processor (I know, I know)

---

### Post by thezood on 2009-08-07
> **payko526 said:**
> I installed 9.04 on an old laptop of mine, and I linked it to my wireless (N) network.  It works some days, but others it gets stuck in a loop where it asks me for the password to my (WPA-TKIP) secured router.  I'm not sure what's happening, because I still get sporadic incidents where it works perfectly, but other days it just loops.

More info, in case I've left anything out:
Wireless-G card
Intel Celeron-M processor (I know, I know)

Are you using ndiswrapper?

---

### Post by 3rdalbum on 2009-08-07
> **payko526 said:**
> More info, in case I've left anything out:
Wireless-G card

Need much more information than that - there's about a hundred different Wireless G chipsets out there, if not more.

The "lspci" and "lsusb" commands should give us some info on exactly what the wireless device is.

---

