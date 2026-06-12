---
title: "Do I have 32 or 64 bit?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by EGamerHDK on 2011-05-03
Should be an easy "problem" to fix. I downloaded 32 bit onto my thumb drive but, when I look at the System Monitor it's telling me it sees 7.8 gigs. Which is what I have installed, but I thought only 64 bit could handle that...

---

### Post by Frogs Hair on 2011-05-03
```
uname -a
``` will display what version you are running.

---

### Post by tgm4883 on 2011-05-03
Through the black magic of PAE, a 32-bit system can see all 8 GB of your memoty

---

### Post by corncob on 2011-05-03
If you see more than one processor in that System Monitor you looked at, I would say 64 bit.  You could type lshw in the terminal and see if width=32 or 64.

---

### Post by K_45 on 2011-05-03
```
uname -m
```

---

### Post by EGamerHDK on 2011-05-04
Alright I'll edit this post when I'm back on my laptop to see if it works. Thanks guys.

---

### Post by corncob on 2011-05-04
> **K_45 said:**
> ```
uname -m
```

Good info and I'll be using it but that just tells you about the operating system.  You could be running 32 bit Linux on a 64 bit computer.

---

### Post by scottuss on 2011-05-04
> **corncob said:**
> If you see more than one processor in that System Monitor you looked at, I would say 64 bit.  You could type lshw in the terminal and see if width=32 or 64.

I have an old Dell laptop that shows up as two CPUs but isn't 64 bit ;)

---

### Post by migs73 on 2011-05-04
Ubuntu 32bit automagically install the PAE kernel when it sees more than 4GB of RAM. This explains how you have installed the 32bit version and have the total RAM available.
PAE can see upto 32GB but can be slightly slower than the standard kernel.

---

### Post by K_45 on 2011-05-04
> **corncob said:**
> Good info and I'll be using it but that just tells you about the operating system.  You could be running 32 bit Linux on a 64 bit computer.

Try it with the -r switch too, which will give you kernel version info.

---

### Post by Paqman on 2011-05-04
> **corncob said:**
> Good info and I'll be using it but that just tells you about the operating system.  You could be running 32 bit Linux on a 64 bit computer.

The OP was asking which version of the OS he had installed, not what their hardware was.

---

### Post by EGamerHDK on 2011-05-05
Alright, so it says i386... so that means I'm running 32 bit Ubuntu. Hah. I'll upgrade to 64 within a few weeks.

---

