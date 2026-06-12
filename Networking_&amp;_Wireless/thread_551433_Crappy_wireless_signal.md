---
title: "Crappy wireless signal"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by ahlt on 2007-09-15
I got a laptop with a Intel pro 3945agb wireless card. But the signal level is extremely poor. When I put my laptop right in front of my access point I only get about 50% signal level. And in my basement, where my mate gets 75% signal (iBook) I don't find the network at all.

What could I do about this? I've read in the man pages for iwconfig, and tried adjusting the rate, txpower and sens. Nothing helped:/

---

### Post by peabody on 2007-09-15
I would check if that card is supported via ndis wrapper.  While the open source driver support just keeps getting better with each Ubuntu release, I've noticed that certain drivers, while working, really don't exploit the hardware properly yet.

---

### Post by ahlt on 2007-09-15
I've tried using ndiswrapper. Couldn't get anything working. But how about the driver from Intel?
[http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)

Is this the same driver that Ubuntu uses as default?

---

