---
title: "make dell wireless minicard work for ubuntu"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by swinger144 on 2008-04-02
how can I make it work for ubuntu?

---

### Post by devurandom77 on 2008-04-15
Look at the ndiswrapper package.  Many of these wireless cards are not natively supported under Linux.  ndiswrapper hot-wires the windows NDIS driver for your card into the linux kernel.  It works rather well for most wireless NICs.

---

