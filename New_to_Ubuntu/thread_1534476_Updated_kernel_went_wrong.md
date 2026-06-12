---
title: "Updated kernel went wrong?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Elysius on 2010-07-19
I just updated my kernel from 2.6.32.xx to 2.6.33.xx from [http://kernel.ubuntu.com/~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline"). Because I need trim support for my SSD.

First did the linux-headers....all.deb, linux-headers....generic.deb and last linux-image....deb.

All went well, but now I want to install my ethernet card again (see my previous _[post]("http://ubuntuforums.org/showthread.php?t=1527354")_). But when I give any of these commands, make clean, make, make install etc. It gives me the follow message:

```

make -C .src/ clean
make[1]: Entering directory ' /home/username/Downloads/ar81family/src'
Makefile:105: *** Linux kernel source not configured - missing autoconf.h. Stop .
make[1]: Leaving directory ' /home/username/Downloads/ar81family/src'
make: *** [clean] Error 2

```And I've no idea how to fix that :D
Can anyone assist?

---

### Post by Elysius on 2010-07-24
I solved this, I had to patch the atheros drivers. Because the kernel headers from 2.6.33 are in a different location, after the patching all is good.

As a side note, the drivers work automatically with kernel 2.6.34. Even easier. ;)

---

