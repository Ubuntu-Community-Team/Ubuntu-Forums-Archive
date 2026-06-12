---
title: "got IV_ICV_Failure (crypto) IRQ(s)"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by cseefurth on 2008-01-07
I'm running Xubuntu 7.10 with a D-Link DWL G650+ wireless card, acx v0.3.36 driver (acx111), firmware version 1.2.1.34

My wireless is (or seems to be) working fine. I get an IP assigned, and have a working connection. However, dmesg is being slammed with the following error, which is being logged about every second.

I've searched extensively, but can't find anything that applies to my situation.

```

[57943.328000] acx: got IV_ICV_Failure (crypto) IRQ(s)
[57943.328000] acx: got IV_ICV_Failure (crypto) IRQ(s)
[57967.292000] acx: got IV_ICV_Failure (crypto) IRQ(s)
[57967.292000] acx: got IV_ICV_Failure (crypto) IRQ(s)
[57967.292000] acx: got IV_ICV_Failure (crypto) IRQ(s)
```

Any idea why this is constantly being thrown?

---

### Post by viciouslime on 2008-06-28
I have the same problem, different card and on Ubuntu Hardy 8.04, but same chipset. Anyone know what causes this?

---

