---
title: "Error compiling SiS190 module"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by Digger78 on 2007-12-26
Basically i have the same problem as in [http://ubuntuforums.org/showthread.php?t=482284]("http://ubuntuforums.org/showthread.php?t=482284")

I have followed his instructions but when i try to compile the module i get the following

```
digger@digger-laptop:/usr/src/linux-source-2.6.22$ sudo make drivers/net/sis190.ko
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CALL    scripts/checksyscalls.sh
/bin/sh: cannot create .tmp_versions/sis190.mod: Directory nonexistent
make[1]: *** [drivers/net/sis190.o] Error 2
make: *** [drivers/net/sis190.ko] Error 2
```

I'm running kubuntu 7.10 on a fujitsu siemens esprimo mobile V5515.

Any ideas about what i need to do to get this compiled?

Thanks

---

### Post by davidgouzien on 2008-01-19
I have the same problem.
Did you find out how to finish the compliation ?

Thanks

---

### Post by Digger78 on 2008-01-20
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I was unable to compile the driver on its own, I had to compile a new kernel with the necessary changes in sis190.c

Do you have the same laptop or just having the same compile problem on another system?

If you have a fujitsu siemens esprimo mobile V5515, I will happily upload the kernel-image & kernel-headers .deb's if you want them.

---

