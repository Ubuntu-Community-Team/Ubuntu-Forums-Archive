---
title: "Where are the drivers stored in ubuntu?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-12-22
What directory are the drivers located in for ubuntu? (specifically, I need to take drivers from a live cd, and patch them into another distro)

---

### Post by SlidingHorn on 2008-12-22
if I remember correctly, they're in /lib/modules/

---

### Post by hyper_ch on 2008-12-22
I don't you can just use the binary drivers and use them in another distro. you'd need to compile them from source for that other distro.

---

### Post by scorp123 on 2008-12-22
> **B34ST1Y said:**
> I need to take drivers from a live cd, and patch them into another distro This does not work like that. You have to take the kernel sources, and then recompile it with the hardware support patches and driver options that you need.

BTW, it would help if you could give more details ... What exactly are you trying to do? And why do you think do you have to do this??

---

