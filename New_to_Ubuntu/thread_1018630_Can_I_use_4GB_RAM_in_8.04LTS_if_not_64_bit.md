---
title: "Can I use 4GB RAM in 8.04LTS if not 64 bit?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by suomalainen on 2008-12-22
Ubunteros,

I've been having a lot of issues with Ubuntu 8.04 LTS 64 bit.

So now I'm deciding if I should move to the 32 bit version instead of the 64. But....

Can I still use all 4GB of RAM in a 32 bit version????

Thanks!

---

### Post by ibizatunes on 2008-12-22
I run for 4GB of memory on a x32 system, it only see 3.5GB - that is the maxium on 32bit system
I have 8.10 but that shouldnt make any difference!

---

### Post by any.linux12 on 2008-12-22
yes no problem...I have one with 5GB (2x512MB and 2x2GB)

---

### Post by Duck2006 on 2008-12-22
Yes, the kernel work ok with 4Gb of ram, To get 32 bit to work you need to compile the kernel to work.

---

### Post by suomalainen on 2008-12-22
Duck2006,

What does it mean to compile the Kernel? Is this something that if I screw up the entire machine dies????

What is involved in compiling a kernel.?

Do I simply use sudo commands in Terminal????

---

### Post by any.linux12 on 2008-12-22
this is my system

see the Attached file

---

### Post by Duck2006 on 2008-12-22
> **suomalainen said:**
> Duck2006,

What does it mean to compile the Kernel? Is this something that if I screw up the entire machine dies????

What is involved in compiling a kernel.?

Do I simply use sudo commands in Terminal????

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by suomalainen on 2008-12-22
Ubunteros,

Do I need to recompile the Kernel if I download from Ubuntu the latest version of 8.04 LTS 32 bit?

Thanks

---

### Post by Duck2006 on 2008-12-22
> **suomalainen said:**
> Ubunteros,

Do I need to recompile the Kernel if I download from Ubuntu the latest version of 8.04 LTS 32 bit?

Thanks

As far as i know yes you will have to compile the kernel.

---

### Post by sdennie on 2008-12-22
See this thread: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by suomalainen on 2008-12-22
Thanks VOR, this information adds greater insight and allows one to understand available options to make a better informed decision!

---

### Post by Captain_tux on 2008-12-22
> **suomalainen said:**
> Ubunteros,

Do I need to recompile the Kernel if I download from Ubuntu the latest version of 8.04 LTS 32 bit?

Thanks

If you want to use 4GB of RAM with Hardy 32 bit... yes.

---

### Post by sdennie on 2008-12-22
> **Captain_tux said:**
> If you want to use 4GB of RAM with Hardy 32 bit... yes.

That's not true.  Again, see: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by oldos2er on 2008-12-22
> **Captain_tux said:**
> If you want to use 4GB of RAM with Hardy 32 bit... yes.

 The (32-bit) server kernel can use that much RAM, it has PAE enabled.

---

