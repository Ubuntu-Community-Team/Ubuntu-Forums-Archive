---
title: "Compiling VIA Velocity™ VT6120, VT6122, 6130, 6132 driver V1.30 on 2.6.24-21"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by yongjunj on 2008-11-07
Hi all,

I'm attaching a patch for the latest driver (V1.30) for VIA Velocity&#8482; VT6120, VT6122, 6130, 6132 Gigabit Ethernet Controllers ([http://www.viaarena.com/Driver/velocity_driver_v31_via.zip](http://www.viaarena.com/Driver/velocity_driver_v31_via.zip)) I created for myself, in case someone is having trouble compiling it on recent kernels. You can apply the patch by typing while in the source directory
```
patch -p1 < /path/to/Velocity_1.30_for_2.6.24-21-generic.patch
```

I've had to go through a few articles online, but Spiffed's article on [http://spiffie.org/computing/archives/2007/08/velocityget_2622.html](http://spiffie.org/computing/archives/2007/08/velocityget_2622.html) proved the most helpful.

The makefile should produce "velocityget" kernel module after "make", and you can install it using "sudo make install".

Depending on your configuration, you may have to modify /etc/modprobe/{aliases, blacklist} to prevent the default "via-velocity" module from loading. If "via-velocity" keeps getting loaded instead of "velocityget", check to see if /initrd.img points to valid, current initrd file.

Note: I've observed that "sudo make install" does "depmod -a", but not necessarily "update-initramfs -u", so you may have to do this manually also.

---

