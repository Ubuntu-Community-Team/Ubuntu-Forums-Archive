---
title: "Awus036h"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Geomancer626 on 2008-11-24
Could anyone explain to me how to replace the default Ubuntu wireless driver for this device with the one from Backtrack 3?

EDIT: Actually, I think my problem lies in that my internal wireless card using an rtl8187b chipset is somehow interfering with the awus036h. However, I am unable to turn off the internal card. Even when I disable it through bios, it still shows found networks in the network manager.

---

### Post by Geomancer626 on 2008-11-29
BUMP

Still haven't resolved the issue. Any help would be greatly appreciated.

---

### Post by elewton on 2008-12-16
I'm in a similar situation.  Using an EEE PC 901 and the AWUS036H not only doesn't work well in ubuntu, but it also interferes with the internal wireless.

The AWUS works perfectly with Backtrack 3.  Using airdriver-ng under ubuntu fails.

Ill post if I get it working.

---

### Post by PokerFacePenguin on 2009-02-11
> **Geomancer626 said:**
> Could anyone explain to me how to replace the default Ubuntu wireless driver for this device with the one from Backtrack 3?

EDIT: Actually, I think my problem lies in that my internal wireless card using an rtl8187b chipset is somehow interfering with the awus036h. However, I am unable to turn off the internal card. Even when I disable it through bios, it still shows found networks in the network manager.

Have you tried compiling the loadable kernel module here :

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

Don't know if that will help or not.  Just a thought.

---

### Post by nuchdog on 2010-03-17
For me the problem in ubntu 9.10 is that the new rtl drivers and the old legacy drivers were both loading. I blacklisted one.  In general, try this tutorial to switch between the two and see which works for you.

[http://forum.aircrack-ng.org/index.php?topic=5755.0]("http://forum.aircrack-ng.org/index.php?topic=5755.0")

---

