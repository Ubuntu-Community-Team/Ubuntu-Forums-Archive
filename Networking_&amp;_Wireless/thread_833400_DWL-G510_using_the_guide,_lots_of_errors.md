---
title: "DWL-G510 using the guide, lots of errors"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Majin_Buu on 2008-06-18
I'm trying this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

and right after "Finally, execute make to build the module. 
$ make all"


```
greenfish@skynet:~/RT61_Linux_STA_Drv1.1.0.0/Module$ make all

make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2

```

---

### Post by chili555 on 2008-06-18
Please try:```
KBUILD_NOPEDANTIC=1 make all
```Post back so the searchers will know, please.

---

### Post by Majin_Buu on 2008-06-19
> **chili555 said:**
> Please try:```
KBUILD_NOPEDANTIC=1 make all
```Post back so the searchers will know, please.

hi! thanks but alas :(

```
greenfish@skynet:~/RT61_Linux_STA_Drv1.1.0.0/Module$ KBUILD_NOPEDANTIC=1 make al
l
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/greenfish/RT61_Linux_
STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function &#8216;RT61_                                                                                                                                                            probe&#8217;:
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:141: error: implici                                                                                                                                                            t declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:216: warning: passi                                                                                                                                                            ng argument 1 of &#8216;dev_get_by_name&#8217; from incompatible pointer type
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:216: error: too few                                                                                                                                                             arguments to function &#8216;dev_get_by_name&#8217;
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function &#8216;RT61_                                                                                                                                                            open&#8217;:
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:328: error: &#8216;SA_SHI                                                                                                                                                            RQ&#8217; undeclared (first use in this function)
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:328: error: (Each u                                                                                                                                                            ndeclared identifier is reported only once
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:328: error: for eac                                                                                                                                                            h function it appears in.)
/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:328: warning: passi                                                                                                                                                            ng argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[2]: *** [/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Erro                                                                                                                                                            r 1
make[1]: *** [_module_/home/greenfish/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2
```

---

### Post by Majin_Buu on 2008-06-20
bump

---

### Post by ikonia on 2008-06-20
has no-one noticed your using instructions for 6.10 - I think things may be reasonably different in 08.04

---

### Post by chili555 on 2008-06-20
> **ikonia said:**
> has no-one noticed your using instructions for 6.10 - I think things may be reasonably different in 08.04
Indeed. The instructions do say to download the latest version, however, the original poster downloaded version 1.1.0.0. I downloaded version 1.1.2.1 and it 'makes' with a few warnings, but no errors on my 2.6.24-19 machine.

---

