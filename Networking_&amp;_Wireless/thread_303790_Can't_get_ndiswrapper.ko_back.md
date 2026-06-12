---
title: "Can't get ndiswrapper.ko back"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by DanielNuyu on 2006-11-20
6.10 and I'm trying to get ndiswrapper working. I deleted the ndiswrapper.ko file following the instructions of one thread, but now I can't get it back. The driver (for the bcom 4306) is loaded, but when I modprobe ndiswrapper I get "no such file" (of course), and when I do ndiswrapper -m I get "modprobe config already contains alias directive." Any suggestions on how to fix this issue?

---

### Post by DanielNuyu on 2006-11-20
Scratch that. I just recompiled a fresh copy of a ndiswrapper 1.28 and all is well.

---

