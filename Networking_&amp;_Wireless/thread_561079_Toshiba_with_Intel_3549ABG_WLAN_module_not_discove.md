---
title: "Toshiba with Intel 3549ABG: WLAN module not discovered"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by DrTha on 2007-09-27
Hi all,

I have a Toshiba with internal WLAN module Intel 3549ABG. I installed Ubuntu 2.6.20-16. WLAN HW was discovered and worked fine.

I compiled my own kernel and installed the new kernel. Since then, the 'old' kernel 2.6.20-16 does not discover the internal WLAN module Intel 3549ABG anymore. Driver is part of the kernel and is running (checked with lsmod).

Inserting a PCMCIA WLAN card (Prism 2.5) works fine and is discovered immediately.

What can I do/have to do, that the kernel discovers the Intel WLAN module ?


The self compiled kernel doesn't discover it either, but discover the PCMCIA WLAN module as well.

Thanks
Thomas

---

