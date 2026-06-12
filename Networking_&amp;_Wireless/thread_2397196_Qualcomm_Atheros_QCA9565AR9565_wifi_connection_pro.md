---
title: "Qualcomm Atheros QCA9565/AR9565 wifi connection problem in ubuntu 18.04"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by brianjdsa on 2018-07-26
Hi,I have recently installed Ubuntu 18.04 on my laptop ASUS with a  Qualcomm Atheros QCA9565/AR9565 wifi card. I tried to install dual system with my windows 10 and Ubuntu in 2 different hard drives.The problem is that wifi can detect other networks but fail to connect to any of them. And the wifi works perfectly in my windows 10. I have done the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info") diagnosis and the result is [http://paste.ubuntu.com/p/J3dbCqyzpX/](http://paste.ubuntu.com/p/J3dbCqyzpX/)  Have tried to install the backports driver but I don't know whether I've successfully installed it with the following warning massages. 
```
root@d-GL552VW:~# cd /home/d/123/backports-4.2.6-1
root@d-GL552VW:/home/d/123/backports-4.2.6-1# make defconfig-ath9k
make[2]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
root@d-GL552VW:/home/d/123/backports-4.2.6-1# make
make[5]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/d/123/backports-4.2.6-1/compat/main.o
  CC [M]  /home/d/123/backports-4.2.6-1/compat/lib-average.o
/home/d/123/backports-4.2.6-1/compat/lib-average.c: In function &#8216;backport_ewma_add&#8217;:
/home/d/123/backports-4.2.6-1/compat/lib-average.c:56:27: error: implicit declaration of function &#8216;ACCESS_ONCE&#8217;; did you mean &#8216;__READ_ONCE&#8217;? [-Werror=implicit-function-declaration]
  unsigned long internal = ACCESS_ONCE(avg->internal);
                           ^~~~~~~~~~~
                           __READ_ONCE
/home/d/123/backports-4.2.6-1/compat/lib-average.c:58:29: error: lvalue required as left operand of assignment
  ACCESS_ONCE(avg->internal) = internal ?
                             ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/d/123/backports-4.2.6-1/compat/lib-average.o' failed
make[6]: *** [/home/d/123/backports-4.2.6-1/compat/lib-average.o] Error 1
scripts/Makefile.build:606: recipe for target '/home/d/123/backports-4.2.6-1/compat' failed
make[5]: *** [/home/d/123/backports-4.2.6-1/compat] Error 2
Makefile:1552: recipe for target '_module_/home/d/123/backports-4.2.6-1' failed
make[4]: *** [_module_/home/d/123/backports-4.2.6-1] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[3]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
root@d-GL552VW:/home/d/123/backports-4.2.6-1# sudo make install
  CC [M]  /home/d/123/backports-4.2.6-1/compat/lib-average.o
/home/d/123/backports-4.2.6-1/compat/lib-average.c: In function &#8216;backport_ewma_add&#8217;:
/home/d/123/backports-4.2.6-1/compat/lib-average.c:56:27: error: implicit declaration of function &#8216;ACCESS_ONCE&#8217;; did you mean &#8216;__READ_ONCE&#8217;? [-Werror=implicit-function-declaration]
  unsigned long internal = ACCESS_ONCE(avg->internal);
                           ^~~~~~~~~~~
                           __READ_ONCE
/home/d/123/backports-4.2.6-1/compat/lib-average.c:58:29: error: lvalue required as left operand of assignment
  ACCESS_ONCE(avg->internal) = internal ?
                             ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/d/123/backports-4.2.6-1/compat/lib-average.o' failed
make[5]: *** [/home/d/123/backports-4.2.6-1/compat/lib-average.o] Error 1
scripts/Makefile.build:606: recipe for target '/home/d/123/backports-4.2.6-1/compat' failed
make[4]: *** [/home/d/123/backports-4.2.6-1/compat] Error 2
Makefile:1552: recipe for target '_module_/home/d/123/backports-4.2.6-1' failed
make[3]: *** [_module_/home/d/123/backports-4.2.6-1] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:40: recipe for target 'install' failed
make: *** [install] Error 2
root@d-GL552VW:/home/d/123/backports-4.2.6-1# 

```

Hopefully I can find some ways to solve the problem.

Thanks for all your help.

Brian

---

