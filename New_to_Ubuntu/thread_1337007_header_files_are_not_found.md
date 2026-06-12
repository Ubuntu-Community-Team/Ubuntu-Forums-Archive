---
title: "header files are not found"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by nilay.linux on 2009-11-25
hi all,

I just got upgraded from Intrepid (8.10) to Karmic (9.10) and having trouble now compiling my driver code as it is not able to find the files.

I did install build-essential, libc6-dev, autoconf, automake, libtool packages. I created a /usr/src/linux link to point to /usr/src/linux-headers-2.6.31-14-generic folder.

I get following errors to start with (its a long dump but lets start from the start):

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /home/nilay/.../linux/kernel_2.6/linux/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/nilay/..../crypto_main.o
cc1: error: include/linux/autoconf.h: No such file or directory
In file included from include/linux/types.h:11,
                 from include/linux/prefetch.h:13,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/nilay/..../crypto_main.c:58:
include/linux/posix_types.h:47:29: error: asm/posix_types.h: No such file or directory
In file included from include/linux/prefetch.h:13,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/nilay/..../crypto_main.c:58:
include/linux/types.h:12:23: error: asm/types.h: No such file or directory
In file included from include/linux/prefetch.h:13,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,

Please help me to get all the header files set up to move ahead with such driver compilations.

Thanks!!
Nilay

---

### Post by mikewhatever on 2009-11-25
Just install the linux-headers-generic metapackage, and it should pull in the appropriate headers for your current kernel.

---

### Post by nilay.linux on 2009-11-26
Thanks mike!!
My fault ... the linux source needs to be compiled first and its all working after I did that.

---

### Post by polax on 2010-04-22
And how exactly do you do that?

---

