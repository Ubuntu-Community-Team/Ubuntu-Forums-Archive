---
title: "Linux kernel???????"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Art3mis on 2009-02-15
Hi everyone,


After searching various Forums and google, I still don't get
what a kernel is and why some people prefer to make their own.


Could anyone pls tell me, I am very new to Linux

---

### Post by logos34 on 2009-02-15
Here's an interesting overview:

[http://www.ibm.com/developerworks/linux/library/l-linux-kernel/](http://www.ibm.com/developerworks/linux/library/l-linux-kernel/)
> 
What is a kernel?
...a kernel is really nothing more than a resource manager. Whether the resource being managed is a process, memory, or hardware device, the kernel manages and arbitrates access to the resource between multiple competing users (both in the kernel and in user space).

People make their own in order to get hardware support (by including the corresponding drivers and modules), or to improve performance, among other things.

---

### Post by Art3mis on 2009-02-15
This might sound really far-fetched for a Linux beginner like me,


but I got a distro (not ubuntu), which still dosen't have Wi-Fi support, is it possible to enable wifi support?

If how? I would like to try, (everyone starts somewhere)

---

### Post by supersonicdarky on 2009-02-15
People generally don't make their own kernels. That is quite a huge undertaking. You may be refering to custom compiling (select which modules you want compiled, as to reduce resource usage) or writing their own modules/drivers/patches for the existing kernel.

And writing your own driver is not as easy as you might think.

---

### Post by logos34 on 2009-02-16
> **supersonicdarky said:**
> ...You may be refering to custom compiling (select which modules you want compiled, as to reduce resource usage) or writing their own modules/drivers/patches for the existing kernel.

that's what I thought the OP meant...

> And writing your own driver is not as easy as you might think.

actually it's not that hard at all, especially if you use soemthing like [KernelCheck]("http://kcheck.sourceforge.net/"), which automates the process while allowing you to customize modules via xconfig.  The twist comes  afterward, i.e. in getting your video driver, wifi/networking, or whatnot to  work properly (I've always been unable to compile the proprietary nvidia graphics driver against the custom kernel)

---

### Post by ferdostar on 2009-02-16
Check the **[this ]("http://www.makelinux.net/kernel_map")** ;)

---

