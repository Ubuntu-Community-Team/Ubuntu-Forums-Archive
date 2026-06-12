---
title: "Kernel source code"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-02-14
This may sound stupid, but I would like to look at the source code for my kernel 2.6.27.11-generic x86_64   I just got a book from the library "Understanding the Linux Kernel" a O'Reilly book. I know the source code is here somewhere. I just don't know where to look. Is it in a file I can open or...?

---

### Post by cerealtx on 2009-02-14
> **S0m3th1ngw13rd said:**
> This may sound stupid, but I would like to look at the source code for my kernel 2.6.27.11-generic x86_64   I just got a book from the library "Understanding the Linux Kernel" a O'Reilly book. I know the source code is here somewhere. I just don't know where to look. Is it in a file I can open or...?

[http://www.kernel.org/](http://www.kernel.org/)

google is your friend

---

### Post by kellemes on 2009-02-14
[http://www.kernel.org/pub/linux/kernel/v2.6/]("http://www.kernel.org/pub/linux/kernel/v2.6/")

The source will be in the tarball I guess..

---

### Post by niteshifter on 2009-02-14
Hi,

The kernel source is also in the repositories. In Synaptic, search for "linux-source", also search for "linux-headers-generic".

After downloading, the source (a tarball) can be found at:
/usr/src/linux-source-2.6.XX.tar.bz2, XX = two digits (your specific kernel base). The headers will also be in /usr/src.

What's the difference between those in the repos and what you get from kernel.org? The ones from kernel.org are the "generics", these are the basis from which every distribution out there builds from. The one from the repos have Ubuntu kernel dev's patches.

This will matter if you move from study to the tinker with stage :)

---

