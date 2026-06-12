---
title: "External HD that was recognized before now won't mount"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by lefthandpath on 2009-08-04
Hi, I've been on Ubuntu for 6 or so months and have always been able to google any problems I had, but this one is a tad different.  I had a external hard drive that ubuntu won't recognize at all, but heres the weird thing.  I've been using it just fine recently (worked two days ago), but now it won't.  It hasn't been connected to any other computer since then and last time used I made sure to unmount it before unplugging it.  Heres what dmesg gives me

> [   89.001037] Clocksource tsc unstable (delta = -277831988 ns)
[  106.544062] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  121.660070] usb 1-2: device descriptor read/64, error -110
I'm running 9.04. BTW.  Thanks.

---

### Post by nothingspecial on 2009-08-04
Have you tried manually mounting it and fsck?

---

