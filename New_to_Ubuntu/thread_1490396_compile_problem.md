---
title: "compile problem"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by hadi3457 on 2010-05-22
Hello
I use 9.10 and when I get updates, I lose my usb modem so I work with 9.10 without updates. I like go to 10.4 and stay on it (my system don't support higher upgrades) but I have this problem in 10.4 too.
I submit a bug in lunchpad too:
[https://bugs.launchpad.net/ubuntu/+bug/573501](https://bugs.launchpad.net/ubuntu/+bug/573501)
now I think problem maybe from Kernel upgrades in updates and if I compile plugin from source I can use of my modem again but I have this problem with compile:

in terminal I go to root and do:
```

./configure

``` 
in source directory and then:
make
```

Making all in eci-common
make[1]: Entering directory `/home/zxc/Downloads/eciadsl-usermode-0.12/eci-common'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/zxc/Downloads/eciadsl-usermode-0.12/eci-common'
make[1]: Entering directory `/home/zxc/Downloads/eciadsl-usermode-0.12'
gcc -DPACKAGE_NAME=\"eciadsl-usermode\" -DPACKAGE_TARNAME=\"eciadsl-usermode\" -DPACKAGE_VERSION=\"0.12\" -DPACKAGE_STRING=\"eciadsl-usermode\ 0.12\" -DPACKAGE_BUGREPORT=\"eci@ml.free.fr\" -DPACKAGE=\"eciadsl-usermode\" -DVERSION=\"0.12\" -DHAVE_LIBPTHREAD=1 -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_FCNTL_H=1 -DHAVE_LIMITS_H=1 -DHAVE_STDINT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_SYS_IOCTL_H=1 -DHAVE_SYS_SOCKET_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_TERMIOS_H=1 -DHAVE_UNISTD_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DRETSIGTYPE=void -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_ALARM=1 -DHAVE_GETTIMEOFDAY=1 -DHAVE_MEMSET=1 -DHAVE_SELECT=1 -DHAVE_SOCKET=1 -DHAVE_STRCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRTOUL=1 -DHAVE_UNAME=1 -I.  -DETC_DIR=\"/etc\" -DCONF_DIR=\"/etc/eciadsl\" -DDOC_DIR=\"/usr/local/share/doc/eciadsl\" -DBINDIR=\"/usr/local/bin\"   -g -O2 -MT pusb.o -MD -MP -MF .deps/pusb.Tpo -c -o pusb.o pusb.c
In file included from pusb.c:13:
pusb-linux.c:32:22: error: asm/page.h: No such file or directory
In file included from pusb.c:13:
pusb-linux.c: In function ‘pusb_endpoint_rw’:
pusb-linux.c:441: error: ‘PAGE_SIZE’ undeclared (first use in this function)
pusb-linux.c:441: error: (Each undeclared identifier is reported only once
pusb-linux.c:441: error: for each function it appears in.)
make[1]: *** [pusb.o] Error 1
make[1]: Leaving directory `/home/zxc/Downloads/eciadsl-usermode-0.12'
make: *** [all-recursive] Error 1

```
in 10.4 I haven't Internet connection so if it require any packages for down load please give me a link for download them manually.
In additional I use of this plug-in for connect:
[http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)
It have a patch for 2.6.x Kernels. Do you know I must use of it or no? and if yes how I can compile it with main source?

Thank you very much

---

### Post by ubudog on 2010-05-22
Open a terminal and type ```
sudo apt-get install build-essential
```

---

### Post by hadi3457 on 2010-05-22
I think it is install:
```

apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libk3b6 libqtscript4-core libqtscript4-gui libqtscript4-uitools
  libqtscript4-sql libqtscript4-xml libqtscript4-network
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 258 not upgraded.

```

---

### Post by ubudog on 2010-05-22
Yeah, it is apparently.  Maybe someone else here can help.  Anyone?

---

### Post by hadi3457 on 2010-05-24
Anyone have no idea?

---

### Post by mc4man on 2010-05-24
> usb-linux.c:32:22: error: asm/page.h:No such file or directory


That (page.h) is a kernel header that you do have - so your source, as is, isn't compatible with the current kernel in 10.04
It would appear the patch in your link is old and wouldn't be of any use here - plus any recent kernels are shown as being untested, ect.

Considering kernel updates broke use of your modem in 9.10 it's not likely 10.04 would prove to be any more suitable.

Your best bet may be to return to 9.10 and not allow kernel updates, though you could certainly update most everything else that isn't kernel version dependent.

Or search out for any current solutions, (don't see anything recent from a quick search) or  get yourself a more compatible modem

---

