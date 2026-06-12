---
title: "question about compiling"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by atngplusultra on 2008-12-22
I'm trying to compile some old ALSA drivers in order to get sound (headphones in particular) working on my laptop.

When I perform the "make" step, however, I get this output:
```
make dep
make[1]: Entering directory `/home/andrew/alsa-driver-1.0.14'
make[2]: Entering directory `/home/andrew/alsa-driver-1.0.14/acore'
copying file alsa-kernel/core/memalloc.c
/home/andrew/alsa-driver-1.0.14/utils/patch-alsa: 24: patch: not found
make[2]: *** [memalloc.c] Error 1
make[2]: Leaving directory `/home/andrew/alsa-driver-1.0.14/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/andrew/alsa-driver-1.0.14'
make: *** [include/sndversions.h] Error 2

```

I've navigated through the directories and found the patch that it's saying is not found, so I don't know what the problem is.

---

### Post by snova on 2008-12-22
Install the 'patch' package.

---

### Post by atngplusultra on 2008-12-22
wow, I feel dumb.
thanks, snova.

---

### Post by atngplusultra on 2008-12-23
okay, new issue with this:
```
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/andrew/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/andrew/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/home/andrew/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/home/andrew/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
```

after some googling, I tried doing a 
KBUILD_NOPEDANTIC=1 make
and got:

```

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/andrew/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/andrew/alsa-driver-1.0.14/acore/sgbuf.o
/home/andrew/alsa-driver-1.0.14/acore/sgbuf.c:2:26: error: linux/config.h: No such file or directory
/home/andrew/alsa-driver-1.0.14/acore/sgbuf.c:11:20: error: config.h: No such file or directory
/home/andrew/alsa-driver-1.0.14/acore/sgbuf.c:13:21: error: adriver.h: No such file or directory
make[3]: *** [/home/andrew/alsa-driver-1.0.14/acore/sgbuf.o] Error 1
make[2]: *** [/home/andrew/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/home/andrew/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
```

ideas?

---

