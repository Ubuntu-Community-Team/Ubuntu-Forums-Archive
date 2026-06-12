---
title: "Realtek 8187 Monitor Mode"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by wasert on 2007-07-21
hi

my laptop comes with a realtek 8187 wireless card. Ubuntu recognized it first and loaded the generic drivers. I was having some problems with my connection so I installed ndiswrapper and the win98 drivers, following the instructions on a post in this forum.

My wireless card is working now. However, when I try to run aircrack-ng I get an error saying that ndiswrapper doesn't support monitor mode.

I tried to install  aircrack's  rt8187 driver ([http://www.aircrack-ng.org/doku.php?id=r8187]("http://www.aircrack-ng.org/doku.php?id=r8187")) I do everything on the guide and even though I don't get any error messages during the installation, my card doesn't show up after the installation is completed.

has anyone installed this driver? is that the only way to put the rtl8187 card in monitor mode?

I'd appreciate any help

---

### Post by salvatore001 on 2007-09-04
maybe you have to modprobe the module

```
modprobe r8187
```

i get to that step, but i get unknown symbols error

---

