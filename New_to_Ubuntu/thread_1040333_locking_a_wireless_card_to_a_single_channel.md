---
title: "locking a wireless card to a single channel?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by B34ST1Y on 2009-01-15
How do I set the wireless card to *only* listen on a single channel, in ubuntu?

---

### Post by compiledkernel on 2009-01-16
sudo iwconfig eth0 channel (x)

man iwconfig for further data related to doing such things.

---

