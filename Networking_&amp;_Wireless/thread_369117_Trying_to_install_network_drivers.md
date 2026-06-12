---
title: "Trying to install network drivers"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by headspace on 2007-02-24
I've been trying on and off for the past week to install the Marvell Yukon drivers for my onboard Gigabit ethernet card (Marvell Yukon 88E8056) after many difficulties i'm nearly there!

The problem this time is found in the install.log

> +++ Compile the driver
+++ ==================================* ==

make: Entering directory `/usr/src/linux-headers-2.6.17-10-* generic'

Makefile:450: .config: No such file or directory
Building modules, stage 2.
/usr/src/linux-headers-2.6.17-10-g* eneric/scripts/Makefile.modpost:38* : .config: No such file or directory

make[1]: *** No rule to make target `.config'. Stop.

make: *** [modules] Error 2

make: Leaving directory `/usr/src/linux-headers-2.6.17-10-* generic'

+++ Compiler error

Many thanks to whoever decides to help me.

---

### Post by headspace on 2007-02-24
Anybody at all?

---

