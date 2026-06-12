---
title: "Kernel upgrade issues in 10.10"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by laz777 on 2011-01-26
I am fairly new to Ubuntu. Just installed a new kernel today ( 2.6.23 to 2.6.38 ) and am experiencing some minor issues.
Am running 10.10 Desktop on an Asus eeepc 1005HA.
No hardware issues have popped up, everything seems to be running well. But, when I boot I get this message:
```
[0.004540] /proc/device-tree: can't find root
```I still am able to boot, just takes about 65 seconds as opposed to about 45 with 2.6.23
On shutdown, I hang and have to manually finish the process, but no problems with a restart.
Otherwise, everything seems to be running smoothly. My question, should I take steps to fix the two minor issues, and if so what should I do?
I have searched this forum and googled the error message, no results. Can anyone explain what the boot message means?

---

### Post by davidmohammed on 2011-01-26
? kernel 2.6.23 was the kernel used in Hardy (8.04) - are you sure you are running 10.10?

---

### Post by coffeecat on 2011-01-26
I should imagine by "2.6.23" the OP means 2.6.35-23, but what 2.6.38 means I don't know.

@laz777, the latest stable kernel in Maverick (at the moment) is 2.6.35-24. Please confirm which kernel versions you are referring to.

---

### Post by laz777 on 2011-01-26
you are correct coffeecat: my older kernel was 2.6.35-23
my kernel update is 2.6.38-020638rc2

---

### Post by coffeecat on 2011-01-26
> **laz777 said:**
> my kernel update is 2.6.38-020638rc2

That is a release candidate of a version of the kernel that has not been officially released yet. Why did you install it? Where did you get it?

---

### Post by laz777 on 2011-01-26
I got it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc2-natty/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc2-natty/")

and I installed it to see if I could get better performance. as far as that goes, it *seems* to run a little smoother, after booting.

---

### Post by coffeecat on 2011-01-26
Well, as you can see, it's a testing version for Natty which itself is a testing version of Ubuntu which is currently using  a 3.6.37 kernel. Have you heard of the bleeding edge? You're lucky that there's so little blood loss here. :)

The one advantage of playing with experimental kernels is that you have the regular kernel to fall back on - so long as you don't uninstall it.

Good luck!

---

### Post by laz777 on 2011-01-26
I'm not a total zorch, I still have 2.6.35-23 installed, but needed to change the boot order in grub (holding shift only produced the grub menu about half the time)

---

