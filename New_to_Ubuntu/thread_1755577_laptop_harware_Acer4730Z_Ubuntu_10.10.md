---
title: "laptop harware Acer4730Z Ubuntu 10.10"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by suprasouth on 2011-05-11
Im wondering if you can do something in Ubuntu like "readyboost" is used in windows(USB thumbdrive as a cache memory), and Can I somehow use my external Hard Drive(WD250g 5400) with my eSata as a raid or anything for speed?

---

### Post by Joe of loath on 2011-05-11
Windows readyboost is basically akin to swap in Linux, it's not really useful apart from in emergencies or for programs that don't read/write to memory much. If you already have swap, it won't be very useful. In fact, it will be less useful, since most USB sticks write at below 10mb/s, most hard drives around 20mb/s, and memory up to 1gb/s.

You could set up a raid with an external hard drive, but it would only work when plugged in. Not very practical for a laptop.

---

