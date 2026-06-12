---
title: "EXTRA_CFLAGS error running &quot;make install&quot;"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by InvisibleMan on 2009-06-16
I may have posted this originally in the wrong category. My apologies for the duplication.
---------------------------------

While running "make install" on an Intel driver download, the following error occurred:

make -C /lib/modules/2.6.28-11-server/build SUBDIRS=/home/operator/drivers/e100-3.5.17/src modules
make[1]: Entering directory '/usr/src/linux-headers-2.6.28-11-server'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/operator/drivers/e100-3.5.17/src/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/operatorr/drivers/e100-3.5.17/src] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-2.6.28-11-server'
make: *** [default] Error 2

I've googled a bit and searched the forums, but nothing matches this exactly, and the solutions for the partial matches (EXTRA_CFLAGS vs CFLAGS_EXTRA) don't work. Any ideas, anyone?

---

### Post by ptn107 on 2009-06-16
I'm guessing it's a bug of some type.  The first thing I would try is to do as it asks, i.e. replace every instance of 'CFLAGS' with 'EXTRA_CFLAGS' in the file '/home/operator/drivers/e100-3.5.17/src/Makefile'.

EDIT:
I found this solution.  Try running this instead of make install...
```
KBUILD_NOPEDANTIC=1 make install
```

---

### Post by InvisibleMan on 2009-06-16
Unfortunately, neither worked.

"KBUILD_NOPEDANTIC=1 make install" and "KBUILD_NOPEDANTIC=1 make"
both produced the same error as before.

Replacing CFLAGS with EXTRA_CFLAGS everywhere in Makefile produced the same errors as the unedited Makefile: unknown fields, implicit declaration of a function, INIT_WORK undeclared, etc.

Running "KBUILD_NOPEDANTIC=1 make install" on the edited Makefile showed no difference, same errors.

---

### Post by InvisibleMan on 2009-06-18
Have I stumped everyone in this forum? I find that hard to believe.

---

