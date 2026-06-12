---
title: "Wired Network doesn't start automatically"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by northhillca on 2008-05-17
I just installed PowerPC64 version of 7.10. Only way wired network works is thru "sudo ifup eth0" after booting computer(PS3).

How do I make it start automatically? Thanks.

---

### Post by chili555 on 2008-05-17
Please try amending your */etc/network/interfaces* to look like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Reboot and let us know.

---

### Post by northhillca on 2008-05-17
it works with "auto eth0" line added. Thanks chili555.

---

