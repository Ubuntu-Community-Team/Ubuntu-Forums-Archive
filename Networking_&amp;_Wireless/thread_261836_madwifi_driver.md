---
title: "madwifi driver"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by z987k on 2006-09-20
I just switched from mandriva to ubuntu and I'm trying to set up the madwifi drivers for wireless access.  In mandrake all I did was install the kernel-source package and then make -> make install and everything was good to go.

I think I installed the kernel-source package with synaptic.  However when trying to make madwifi I get 
```
Makefile.inc:113: *** KERNELCONF: /usr/src/linux-source-2.6.15//.config does not exist..  Stop.

```
At first I thought something was messed up because it's looking at //.config but then I looked in the path it's looking for and there is no config file there so obvisouly it can't find it.  What went wrong with the kernel source install or do I need to do something more?

Zach

---

### Post by spd106 on 2006-09-21
You need the kernel headers:-
 linux-headers-386,
 linux-headers-`uname -r`
and probably the build-essential package.

---

### Post by tturrisi on 2006-09-21
madwifi is included in the linux-restricted-modules for your kernel, easily installed via synaptic.

---

### Post by z987k on 2006-09-21
That you!  Didn't even think about looking in synaptec, it's one thing I've always had to compile.

---

