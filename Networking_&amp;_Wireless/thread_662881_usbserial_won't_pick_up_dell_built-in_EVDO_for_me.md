---
title: "usbserial won't pick up dell built-in EVDO for me"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by bimargulies on 2008-01-09
gutsy gibbon.

lsusb tells me  vendor and product for buildin novatel/dell EVDO.

So, I run modprobe ... (as sudo, of course)

modprobe usbserial vendor=0x413c product=0x8133

and nothing happens. no traffic in dmesg, no traffic in /var/log/messages, no errors.

Now what?

---

