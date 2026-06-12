---
title: "Testing a new kernel(how to do it?)"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by mbzn on 2010-06-15
Hi, i have a bug reported on launchpad: bug #293427
Basicly i was asked this:
> If you could also please test the latest upstream kernel available that would be great. It will allow additional upstream developers to examine the issue. Refer to [https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)  . Once you've tested the upstream kernel, please remove the 'needs-upstream-testing' tag. This can be done by clicking on the yellow pencil icon next to the tag located at the bottom of the bug description and deleting the 'needs-upstream-testing' text. Please let us know your results.

So, i want to know if this [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) would be the one i have to try.

I don't have much knowledge of upgrading (to newer than released) kernels

Thanks in advance

---

### Post by mbzn on 2010-06-16
No-one?

---

### Post by Bachstelze on 2010-06-16
The link has a bunch of DEB packages. Download the linux-image package corresponding to your architecture (i386 or amd64) and double-click on it to install the kernel. Then reboot, the new kernel should appear in the boot menu.

---

### Post by mbzn on 2010-06-16
Thanks for the reply, actually I would just like to know whether that would be the right kernel version as I'm asked to test the latest mainline kernel?

EDIT: basically I have these options [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Should i use v2.6.34-lucid/ or should i jump to v2.6.35-rc1-lucid/. As I guess I can help testing both but the rc1 seems really unstable as I believe it's hardly tested.

Also am i right to think that after these installs my 2.6.32-22 kernel would be the same(stable and problem free) as before I install the others?

---

### Post by Bachstelze on 2010-06-16
Yes, that is the most recent one.

---

### Post by mbzn on 2010-06-16
Thanks again

---

### Post by Bachstelze on 2010-06-16
> **mbzn said:**
> 
EDIT: basically I have these options [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Should i use v2.6.34-lucid/ or should i jump to v2.6.35-rc1-lucid/. As I guess I can help testing both but the rc1 seems really unstable as I believe it's hardly tested.

Also am i right to think that after these installs my 2.6.32-22 kernel would be the same(stable and problem free) as before I install the others?

The most recent one will always be at daily/current. If you are asked to test the latest one, that's the one you should get.

---

