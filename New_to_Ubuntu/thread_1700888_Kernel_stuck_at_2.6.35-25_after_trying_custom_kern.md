---
title: "Kernel stuck at 2.6.35-25 after trying custom kernel"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Mobidoy on 2011-03-05
A while ago, I tried to compile a Kernel with a Patch for my notebook subwoofer. The patch did not work so, I reverted back to the official 2.6.35-25 Kernel.

Sadly, since then, I never receive new Kernels. I need to force install them. What can I try out to get them thru normal updates ?

---

### Post by andrewthomas on 2011-03-11
```
sudo apt-get install linux linux-image
```This package will always depend on the latest generic complete Linux kernel available.       

Either one will do, but it doesn't hurt to have them both installed.

---

