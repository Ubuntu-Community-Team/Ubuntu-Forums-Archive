---
title: "How to compile 8139too.c in 2.6.20 kernel"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by ann1 on 2007-10-10
Hi,
I have Realtek 8139D PCI card and it shows in lsmod. I now want to compile 8139too.c (version "0.9.28") to understand the code. However, it does not compile and give lots of error messages.
I am using,
gcc -DMODVERSIONS -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -O6 -c 8139too.c

Can you suggest what am I missing here. I also tried adding include files (-I) from /usr/src/(kernel version)/include.  Am I using wrong version of 8139too.c file (if so, can you please tell the source)?
Thanks,
Ann

---

### Post by Lambert on 2007-10-11
> **ann1 said:**
> Hi,
I have Realtek 8139D PCI card and it shows in lsmod. I now want to compile 8139too.c (version "0.9.28") to understand the code. However, it does not compile and give lots of error messages.
I am using,
gcc -DMODVERSIONS -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -O6 -c 8139too.c

Can you suggest what am I missing here. I also tried adding include files (-I) from /usr/src/(kernel version)/include.  Am I using wrong version of 8139too.c file (if so, can you please tell the source)?
Thanks,
Ann


Post the errors you are getting.

---

### Post by ann1 on 2007-10-11
Thanks. The messages are like:
struct rtl8139_private has no member named "lock"/"pci_dev"/ "rx_ring"/"tx_bufs" and so on. Even though I see these members defined in the struct.

---

### Post by Lambert on 2007-10-11
After thinking about this for a minute, 8139too.c is a statically loaded module so it is compiled into the kernel. 

I'm not that knowledgeable when it comes to compiling but I'm curious if it is possible to do what you're doing? Do you need to compile a new kernel with out this module and then go through the compile process as a dynamic module?

---

### Post by ann1 on 2007-10-11
Yes I do find it as a module 8139too.ko. I am not compiling a new kernel, just this 8139too.c file into 8139too.o and then insmod 8139too.o. Is this fine?
 I am trying to compile in 2.6.20 generic kernel - will generic be a problem.

---

### Post by ann1 on 2007-10-15
Just to tell that I could compile it by using "make all" at /usr/src/linux, which actually compiles everything. Then "make modules_install" loaded the updated driver 8139too.ko.
Ann

---

