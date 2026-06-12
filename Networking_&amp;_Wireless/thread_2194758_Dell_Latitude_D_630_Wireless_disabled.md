---
title: "Dell Latitude D 630: Wireless disabled"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by abhididdigi on 2013-12-20
I'm on Dell Latitude D 630 and installed Ubuntu 13.10. Wireless adapter doesn't show up. Any ideas?

Thanks you!

---

### Post by tfrue on 2013-12-20
Post the output of the commands:

If PCI:
```
lspci
```
If USB:
```
lsusb
```
And also:
```
ifconfig -a
```
Just to get started! :)

---

