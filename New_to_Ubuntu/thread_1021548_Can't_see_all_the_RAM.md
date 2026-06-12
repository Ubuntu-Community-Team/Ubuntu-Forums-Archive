---
title: "Can't see all the RAM"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by orbitfish on 2008-12-25
using the free -m command it seems that I have only 3.3GB RAM; however, I know that there are 4 x 1GB sticks of Crucial DDR2 Ballistix memory installed. Why can't Ubuntu see all the memory?

---

### Post by taurus on 2008-12-25
Are you running the 32bit kernel (i686)?

```
uname -a
```
32bit can only see up to 3.2GB so if you want to use all your RAM, you should consider installing the 64bit (x86_64) version, if your CPU is a 64bit.

---

### Post by igknighted on 2008-12-25
You can also install the server kernel (instead of generic).  It is compiled with PAE (physical address extension IIRC?) which lets a 32bit kernel use up to 64gb of ram, but with some performance hit.

64bit is probably your best bet if your CPU is capable, but would require a reinstall.

---

### Post by jimmy the saint on 2008-12-25
> **taurus said:**
> Are you running the 32bit kernel (i686)?

```
uname -a
```
32bit can only see up to 3.2GB so if you want to use all your RAM, you should consider installing the 64bit (x86_64) version, if your CPU is a 64bit.

That is a common misconception.  32-bit linux can support can support up to 64Gigs of RAM through PAE.  It just requires a kernel option, which is probably beyond the scope of the beginner talk forum.  

OP: Many MOBOs do not support more than 3.2 gigs of RAM. You should check into your MOBO make and model and see if it does.  I have a Gigabyte motherboard which does not support 4 Gigs (even though the box CLEARLY states that it does) so installing 64 bit ubuntu did not solve that issue.

---

### Post by zvacet on 2008-12-25
@ **orbitfish**

[This]("http://ubuntuforums.org/showthread.php?t=855511&highlight=4GB+ram+32+bit") can be interesting to read.

---

### Post by StOoZ on 2008-12-25
why 32bit systems can have only up to 4GB?

---

### Post by igknighted on 2008-12-25
> **StOoZ said:**
> why 32bit systems can have only up to 4GB?

A 32bit processor (and hence, OS) can only understand 32bit chunks at a time.  So any address sent to the CPU to fetch from memory must be able to be uniquely identified by 32 binary bits (either a 0 or a 1).  2^32 (32 binary bits) = 4 GiB.  You actually get a little less than that, because if every command the processor received was a memory address, little would get done.

64bit (2^64) = insanely large address space, hence no issues (in the near future at least) with running out.  It does mean each pointer (points to another spot in memory) is twice as large (32 digits vs. 64), so it takes more memory to store them.  Hence, on low memory systems, 64bit may not be the best idea.

I'm not sure how PAE works.  Hopefully someone can enlighten us?

---

### Post by fouadatmeh on 2008-12-25
PAE works as follows:

The x86 processor hardware is augmented with additional address lines used to select the additional memory, so physical address size is increased from 32 bits to 36 bits. This increases maximum physical memory size from 4 GB to 64 GB. The 32-bit size of the virtual address is not changed, so regular application software continues to use instructions with 32-bit addresses andThe operating system uses page tables to map this 4 GB address space into the 64 GB of RAM

** taken from wikipedia **

---

### Post by igknighted on 2008-12-25
> **fouadatmeh said:**
> PAE works as follows:

The x86 processor hardware is augmented with additional address lines used to select the additional memory, so physical address size is increased from 32 bits to 36 bits. This increases maximum physical memory size from 4 GB to 64 GB. The 32-bit size of the virtual address is not changed, so regular application software continues to use instructions with 32-bit addresses andThe operating system uses page tables to map this 4 GB address space into the 64 GB of RAM

** taken from wikipedia **

Makes sense.  Should also mean that applications are limited to 4gb each, yes?  So if I have GIMP open, it can't use 6gb.  But it can have 4gb and firefox can have 2gb.

Also explains the performance hit.  Anytime you need to grab something from RAM, you need to spend a few cycles using the page tables to find the true address, slowing down the process.

---

### Post by scorp123 on 2008-12-25
> **igknighted said:**
>  Also explains the performance hit.  The performance hit is not so dramatic as some make it to be. Under normal circumstances you shouldn't see or feel anything of that.

---

