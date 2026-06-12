---
title: "RT2500 dissfucntions during building!"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by k-os on 2007-06-24
Well, I've been walking through one how-to after the other, I end up in nowhere and in complete nonsense. I don't get it, I just don't get it to work! So, in this thread I hope someone who knows what to be done can tell me. Reading through post after post on others attempts is not helping me, so if someone know which thread that led to success, show me, or if someone know  how to fix my problem, tell me. Here is how far I get, following this how to from step "4.3. Compile Newer Driver": [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

```
$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/k-os/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /home/k-os/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/home/k-os/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/home/k-os/rt2500-1.1.0-b4/Module/rtmp_main.c: In function &#8216;RT2500_open&#8217;:
/home/k-os/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: *** [/home/k-os/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/k-os/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

```

Help is highly appreciated!

---

### Post by Austin_KW on 2007-06-25
Try the cvs (daily/hourly) tarball from the same download page, should be more upto date.

---

