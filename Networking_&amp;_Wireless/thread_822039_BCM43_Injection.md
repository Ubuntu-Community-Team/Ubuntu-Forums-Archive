---
title: "BCM43 Injection"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by G-Unot on 2008-06-07
Hi guys,

Im on ubuntu 8.04. i was wondering if there is a way that i can use either the bcm43xx-injection-linux-2.6.20.patch or bcm43xx-injection-linux-2.6.22-V2.patch. would these patches still work even if im on 2.6.24? or would i have to downgrade kernels.

g-unot

---

### Post by nixscripter on 2008-06-08
With kernel patches, I just apply them and see what the fuzz factor is. If it's low, and the driver hasn't changed since those versions, cross your fingers; it's usually safe.

This, however, is general advice. The last thing I did this for was the SquashFS patch. Wireless drivers might be a different matter.

---

