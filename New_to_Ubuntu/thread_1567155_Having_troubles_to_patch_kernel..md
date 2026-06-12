---
title: "Having troubles to patch kernel."
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Fanatico on 2010-09-03
I am newbie and trying to learn how to patch Linux kernel.
I've downloaded kernel sources linux-2.6.33.7.tar.bz2 and patch
patch-2.6.34.6.bz2 from [www.kernel.org](www.kernel.org)

I've uncompressed Linux kernel sources and applied patch:
bzcat ../patch-2.6.34.6.bz2 | patch p1

I've received the following error message:
**Reversed (or previously applied) patch detected! Assume -R?**

What could be wrong?

Thanks in advance

---

### Post by andrewthomas on 2010-09-03
> **Fanatico said:**
> 

What could be wrong?


You are applying a 2.6.34 patch to a 2.6.33 kernel. just get the 2.6.34.6 source
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.34.6.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.34.6.tar.bz2)

---

