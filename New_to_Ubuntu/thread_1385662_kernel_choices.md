---
title: "kernel choices"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-19
Hello friends

I have been told that the stock kernel is what we get by default.Are there any choices for
kernels?How do i find out which kernel do i have?

---

### Post by fugaki on 2010-01-19
you can run uname -r in terminal to see the kernel version.
it depends on what you are trying to do for which kernel is best.

---

### Post by FreezWay on 2010-01-19
type "uname -a" to view your kernel info.

You can either
1) keep your current kernel until karmic koala
2) download a pre-built kernel package ([here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/"))
3) compile your own (VERY advanced. I've only done it once)

as for #2 theres a certain order you have to install the packages, but i cant remember.

---

### Post by baddog144 on 2010-01-19
There are various options for alternate kernels, the most versatile of which is compiling your own, but that is also the most intimidating. There are some pre-built ones, at one point there was the Zen kernel, I don't know if that's still going. Personally, I find the stock kernel suits me just fine ;)

---

### Post by lidex on 2010-01-19
> Reasons for compiling a custom kernel

    * You are a kernel developer.
    * You need the kernel compiled in a special way, that the official kernel is not compiled in (for example, with some experimental feature enabled).
    * You are attempting to debug a problem in the stock Ubuntu kernel for which you have filed or will file a bug report.
    * You have hardware the stock Ubuntu kernel does not support. 

Reasons for NOT compiling a custom kernel

    * You merely need to compile a special driver. For this, you only need to install the linux-headers packages.
    * You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.
    * You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels. 

From **[this]("https://help.ubuntu.com/community/Kernel/Compile")** page

---

### Post by sandyd on 2010-01-19
> **manny43 said:**
> Hello friends

I have been told that the stock kernel is what we get by default.Are there any choices for
kernels?How do i find out which kernel do i have?
Theirs several main types of kernels in ubuntu

Generic. - Needs no explanation, this is what your currently using. This kernel is nice for all computers, hence the reason why its called generic.

Realtime - Kernel causes cpu cycles / processes to be done within a specific timeframe. This is only useful for multimedia recording, which is why its used in ubuntu studio.

Xen - Kernel for virtual machines, the kernel supports running multiple Oses at once. Mainly used for VPSes although some companies use it for resource management and thin clients.

Server - Also self explanatory, its designed to be used on servers such as the one that powers this site that im typing on.

Custom kernel - Useful if you need to to kernel source code edits, developping or enabling/disabling some built-in kernel option. Although there is the misconception of it being way faster, its only slightly faster and not worth the effort.  Theirs a link in my sig to build a custom kernel, but please don't do this as you will pull all your hair out before you finish.

---

### Post by 3rdalbum on 2010-01-19
> **manny43 said:**
> I have been told that the stock kernel is what we get by default.

The word "stock", in this instance, means "default" anyway. The kernel we get by default is the default Ubuntu kernel.

---

