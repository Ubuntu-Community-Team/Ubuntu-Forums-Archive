---
title: "Belkin Wireless G USB Adapter."
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by JoeRinaldi on 2007-05-09
I can't seem to get this to work for ubuntu linux :( 7.04

---

### Post by chili555 on 2007-05-10
There are quite a few Belkin USB wireless adapters, each with a different chipset, each needing different methods to get working. Plug it in and please show us, in a terminal:```
sudo lshw -C network
```Thanks.

---

### Post by rich.bradshaw on 2007-05-10
Probably an rt2500. I have one with rt2500, works fine with ndiswrapper (if you don't know what that is, search on this forum/wiki as everyone uses it!) I think there are builtin drivers as well, but I have never had much luck...

---

