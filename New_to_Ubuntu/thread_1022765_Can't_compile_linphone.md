---
title: "Can't compile linphone"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by DexterLB on 2008-12-27
So, I downloaded the latest version of linphone.

The configure script exits successfully and creates the makefiles etc, but running make outputs this error:
```
make  all-recursive
make[1]: Entering directory `/home/main/src/linphone/linphone-3.0.0'
Making all in m4
make[2]: Entering directory `/home/main/src/linphone/linphone-3.0.0/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/m4'
Making all in pixmaps
make[2]: Entering directory `/home/main/src/linphone/linphone-3.0.0/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/pixmaps'
Making all in po
make[2]: Entering directory `/home/main/src/linphone/linphone-3.0.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/po'
Making all in ipkg
make[2]: Entering directory `/home/main/src/linphone/linphone-3.0.0/ipkg'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/ipkg'
Making all in oRTP
make[2]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP'
make  all-recursive
make[3]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP'
Making all in src
make[4]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src'
Making all in .
make[5]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src'
Making all in tests
make[5]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests'
Making all in win_receiver
make[6]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests/win_receiver'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests/win_receiver'
Making all in win_sender
make[6]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests/win_sender'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests/win_sender'
make[6]: Entering directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include/   -D_ORTP_SOURCE -D_REENTRANT  -g -O2 -Wall -Werror   -DORTP_INET6 -MT rtpsend.o -MD -MP -MF ".deps/rtpsend.Tpo" -c -o rtpsend.o rtpsend.c; \
	then mv -f ".deps/rtpsend.Tpo" ".deps/rtpsend.Po"; else rm -f ".deps/rtpsend.Tpo"; exit 1; fi
cc1: warnings being treated as errors
rtpsend.c: In function ‘main’:
rtpsend.c:50: error: format not a string literal and no format arguments
rtpsend.c:57: error: format not a string literal and no format arguments
rtpsend.c:66: error: format not a string literal and no format arguments
make[6]: *** [rtpsend.o] Error 1
make[6]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src/tests'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/main/src/linphone/linphone-3.0.0/oRTP'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/main/src/linphone/linphone-3.0.0'
make: *** [all] Error 2
```

Do you have any idea how to fix this?

---

### Post by DexterLB on 2008-12-27
bump
ah come on! this christmas the only thing I get is BUMP

---

### Post by DexterLB on 2008-12-29
BUMP :sad:

---

### Post by jis on 2009-11-02
I am using Jaunty and get the same thing.

---

### Post by liquidbee on 2009-11-02
```
gcc -v
```

What's the output ?

---

### Post by jis on 2009-11-02
Oh. little bit different:
> 
$ make
make  all-recursive
make[1]: Entering directory `/media/data/src/linphone-3.2.1'
Making all in m4
make[2]: Entering directory `/media/data/src/linphone-3.2.1/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/data/src/linphone-3.2.1/m4'
Making all in pixmaps
make[2]: Entering directory `/media/data/src/linphone-3.2.1/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/data/src/linphone-3.2.1/pixmaps'
Making all in po
make[2]: Entering directory `/media/data/src/linphone-3.2.1/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/data/src/linphone-3.2.1/po'
Making all in oRTP
make[2]: Entering directory `/media/data/src/linphone-3.2.1/oRTP'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/media/data/src/linphone-3.2.1/oRTP'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/data/src/linphone-3.2.1'
make: *** [all] Error 2


---

### Post by jis on 2009-11-02
Output of `gcc -v`:

> 
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 


---

### Post by liquidbee on 2009-11-02
Downgrading to 4.2 should solve the problem.

---

### Post by jis on 2009-11-02
4.2 is not available in Jaunty.

---

### Post by liquidbee on 2009-11-02
> **jis said:**
> 4.2 is not available in Jaunty.

[gcc-4.2 in Jaunty]("http://packages.ubuntu.com/jaunty/gcc-4.2") - still not available ?

---

### Post by jis on 2009-11-02
Oh, it is there. I installed it and changed gcc to link to it. But make still fails with the same output.

---

