---
title: "How to modify the Kernel?"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by zenji agamotto on 2010-12-20
Okay ! so i am just trying to dig into linux, and one of the most popular things to do seems to tell the kernel what to load and what not to load, I have a couple directions telling me to go into /usr/src/linux and make menuconfig which seems to be altered in ubuntu.

specifcally i am trying to load some networking modules like 
CCMP support TKIP etc
Wireless extensions and other modules I meed to put my usb wireless adapter into monitor mode
how do i get into make menuconfig?

---

### Post by stmiller on 2010-12-20
What source are you reading this from? Compiling a custom kernel is generally not needed for wifi drivers.

Have you checked out the backtrack distro?

---

### Post by jtarin on 2010-12-21
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Aero_Zeppelin on 2010-12-21
If you are new to linux,i dont think compiling your own kernel is a good thing to do.Try to keep things simple/stupid for the moment.:) Just my opinion.

---

### Post by jtarin on 2010-12-21
> **Arindam Momin said:**
> If you are new to linux,i dont think compiling your own kernel is a good thing to do.Try to keep things simple/stupid for the moment.:) Just my opinion.
As long as you have a good kernel backup there shouldn't be any problems._**Be prepared to have an un-bootable system**_. If you don't break things you never know how to fix them.

---

### Post by amjjawad on 2010-12-21
> **jtarin said:**
> **If you don't break things you never know how to fix them.**

Couldn't agree more :)

Good to see you back to action again, my friend :)

---

### Post by jtarin on 2010-12-21
> **amjjawad said:**
> Couldn't agree more :)

Good to see you back to action again, my friend :)I lurk! Never entirely gone.;)

---

### Post by QLee on 2010-12-21
[QUOTE=jtarin]I lurk! Never entirely gone.;)[/QUOTE]

And like all good lurkers, you post when you have content pertinent to the discussion. Good for you John, I wish everyone took the same approach. Am almost violating that ideal by posting this but I respect your work and wanted to compliment that.

---

### Post by admiralspark on 2010-12-26
There are many great guides on the internet for compiling your own kernel, here's my humble blog post how-to: [http://admiralspark.blogspot.com/2010/12/compiling-vanilla-linux-kernel-for.html](http://admiralspark.blogspot.com/2010/12/compiling-vanilla-linux-kernel-for.html)

---

