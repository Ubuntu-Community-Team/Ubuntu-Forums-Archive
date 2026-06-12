---
title: "Troubles Compiling ACX111 Module"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by CourtD on 2007-08-27
Hi all! I'm a bit of a linux newb, and as such have a little trouble knowing what's going on.

I was following [this]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111") tutorial on setting up a ACX 111 based WiFi card to work on ubuntu. I got  all the way to step 1.6 where you're asked to compile the module without a hitch. But then when I tried to execute ```
make -C /lib/modules/`uname -r`/build M=`pwd`
```  I got this message:```
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /root/ACX/built-in.o
  CC [M]  /root/ACX/wlan.o
  CC [M]  /root/ACX/conv.o
  CC [M]  /root/ACX/ioctl.o
  CC [M]  /root/ACX/common.o
/root/ACX/common.c:6944:14: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/root/ACX/common.c: In function ‘acx_init_task_scheduler’:
/root/ACX/common.c:6943: error: ‘INIT_WORK’ undeclared (first use in this function)
/root/ACX/common.c:6943: error: (Each undeclared identifier is reported only once
/root/ACX/common.c:6943: error: for each function it appears in.)
make[1]: *** [/root/ACX/common.o] Error 1
make: *** [_module_/root/ACX] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
root@court-laptop:~/ACX# sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules_install
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  DEPMOD  2.6.20-16-generic
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
```

I'm not sure what that means, but I'm pretty sure it's similar to my computer slapping me in the face.

Help please!


Court

---

