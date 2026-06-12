---
title: "Wireless card breaks with new kernel"
date: 2005-08-31
forum: Networking &amp; Wireless
---

### Post by benash on 2005-08-31
Hi, I have a PCI D-Link AirPlus wireless adapter that functions on a 2.6.10-5-386 kernel, but not on the k7 version.  The wlan0 device does not appear in the Administration>Networking tool of Hoary with the k7 kernel.

Additionally, the throughput is quite slow (~33KB.s) with the generic kernel.

Does anyone have any ideas?

Thanks,
Ben

---

### Post by firecat53 on 2005-08-31
Not sure what driver your card uses, but you could attempt downloading the source for your driver and recompiling it.  That's what I had to do with the Madwifi drivers for my DWL-G630. Good luck!

---

