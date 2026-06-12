---
title: "Orinoco Problems with make command"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by dsforsaken on 2007-08-29
im following this guide:
[https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)
the problem happens when i try to run make on either one
 ```

      make -C /usr/src/linux-headers-2.6.20-16-generic M=/home/mike/orinoco-0.15 KERNELRELEASE=2.6.20-16-generic modules.
      make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
      /home/mike/orinoco-0.15/Kbuild:38: *** This driver is already enabled in the kernel.  Stop.
      make[1]: *** [_module_/home/mike/orinoco-0.15] Error 2
      make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
      make: *** [modules] Error 2

```

---

### Post by bmartin on 2007-08-31
This message appears when you're trying to compile a kernel module that's already built into the kernel. See [this page]("http://osdir.com/ml/linux.drivers.orinoco.user/2006-09/msg00002.html").

I'm not sure how to get around the "too strict" problem. Check the output of **lsmod** and see if the orinoco kernel module is there. If so, it can be removed using **sudo modprobe -r orinoco**, or whatever the kernel module name is.

---

