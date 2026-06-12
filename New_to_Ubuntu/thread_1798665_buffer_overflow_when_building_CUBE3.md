---
title: "buffer overflow when building CUBE3"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by ad~ on 2011-07-06
Hi.
I'm trying to install Scalasca's Cube 3.3.2.  When I run make I get a buffer overflow message.  I don't really know what I could have messed up since configure and make are all I've done since downloading and opening the tarball.

Here's the output of make.  I realize this is kind of a specific problem, but I'd appreciate any suggestions about what could have caused this or what to do next.

EDIT:
I realized that I stupidly forgot to try building any other software.  I tried compiling a few other things with make and none of them worked.
> ```
************************************************************
*                      Building CUBE3                      *
************************************************************

---------- utils/stats ----------

make[1]: Entering directory `/home/adriana/cube-3.3.2/utils/stats'
g++ -m32 -O3 -c P2Statistic.cpp 	
ar  -rcs libstats.a P2Statistic.o
*** buffer overflow detected ***: ar terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x50)[0x40117970]
/lib/libc.so.6(+0xe486a)[0x4011686a]
/lib/libc.so.6(+0xe3fa8)[0x40115fa8]
/lib/libc.so.6(_IO_default_xsputn+0x9e)[0x4009ca2e]
/lib/libc.so.6(_IO_padn+0xd8)[0x400903b8]
/lib/libc.so.6(_IO_vfprintf+0x2b17)[0x40071d27]
/lib/libc.so.6(__vsprintf_chk+0xad)[0x4011605d]
/lib/libc.so.6(__sprintf_chk+0x2d)[0x40115f9d]
ar[0x804fb25]
ar[0x804de9b]
ar[0x805050e]
ar[0x8052b72]
ar[0x804b50c]
ar[0x804bff7]
/lib/libc.so.6(__libc_start_main+0xe7)[0x40048ce7]
ar[0x8049491]
======= Memory map: ========
08048000-08089000 r-xp 00000000 08:05 4342540    /usr/local/bin/ar
08089000-0808a000 r--p 00040000 08:05 4342540    /usr/local/bin/ar
0808a000-0808b000 rw-p 00041000 08:05 4342540    /usr/local/bin/ar
09e24000-09e45000 rw-p 00000000 00:00 0          [heap]
40000000-4001c000 r-xp 00000000 08:05 3539774    /lib/ld-2.12.1.so
4001c000-4001d000 r--p 0001b000 08:05 3539774    /lib/ld-2.12.1.so
4001d000-4001e000 rw-p 0001c000 08:05 3539774    /lib/ld-2.12.1.so
4001e000-4001f000 r-xp 00000000 00:00 0          [vdso]
4001f000-40021000 rw-p 00000000 00:00 0 
40021000-40022000 r--p 002a1000 08:05 3934558    /usr/lib/locale/locale-archive
40022000-40025000 rw-p 00000000 00:00 0 
40032000-40189000 r-xp 00000000 08:05 3539777    /lib/libc-2.12.1.so
40189000-4018b000 r--p 00157000 08:05 3539777    /lib/libc-2.12.1.so
4018b000-4018c000 rw-p 00159000 08:05 3539777    /lib/libc-2.12.1.so
4018c000-40190000 rw-p 00000000 00:00 0 
40190000-40390000 r--p 00000000 08:05 3934558    /usr/lib/locale/locale-archive
403a1000-403bb000 r-xp 00000000 08:05 3539023    /lib/libgcc_s.so.1
403bb000-403bc000 r--p 00019000 08:05 3539023    /lib/libgcc_s.so.1
403bc000-403bd000 rw-p 0001a000 08:05 3539023    /lib/libgcc_s.so.1
bfec7000-bfee8000 rw-p 00000000 00:00 0          [stack]
make[1]: *** [libstats.a] Aborted
make[1]: *** Deleting file `libstats.a'
make[1]: Leaving directory `/home/adriana/cube-3.3.2/utils/stats'
make: *** [all] Error 2
```


---

