---
title: "Problem compiling kernel"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Varnius on 2011-01-31
Hi guys,
 I`ve decided to set up a few game servers and followed a [tutorial]("http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization") for compiling custom kernel in order to get maximum performance gain for the servers. The problem is after I try to compile the kernel using
```
make-kpkg --initrd kernel_image kernel_headers
```the compilation goes on for some time and then I get a bunch of errors:

```

  CC [M]  drivers/staging/comedi/drivers/quatech_daqp_cs.o
drivers/staging/comedi/drivers/quatech_daqp_cs.c: In function \u2018daqp_interrupt\u2019:
drivers/staging/comedi/drivers/quatech_daqp_cs.c:308: error: implicit declaration of function \u2018up\u2019
drivers/staging/comedi/drivers/quatech_daqp_cs.c: In function \u2018daqp_ai_insn_read\u2019:
drivers/staging/comedi/drivers/quatech_daqp_cs.c:421: error: implicit declaration of function \u2018sema_init\u2019
drivers/staging/comedi/drivers/quatech_daqp_cs.c:434: error: implicit declaration of function \u2018down_interruptible\u2019
make[5]: *** [drivers/staging/comedi/drivers/quatech_daqp_cs.o] Error 1
make[4]: *** [drivers/staging/comedi/drivers] Error 2
make[3]: *** [drivers/staging/comedi] Error 2
make[2]: *** [drivers/staging] Error 2
make[1]: *** [drivers] Error 2

```The kernel version I`m compiling is 2.6.31.12. (Patch 2.6.31.12-rt21)

---

