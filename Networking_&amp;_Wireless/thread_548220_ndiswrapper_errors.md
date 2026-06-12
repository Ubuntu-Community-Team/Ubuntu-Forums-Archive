---
title: "ndiswrapper errors"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by bardoksan on 2007-09-11
I am trying to get ndiswrapper installed on a brand new install of kubuntu.  I've searched around and have found some detailed install instructions, but I get error messages when I do the install. After I downloaded and extracted the tarball, I started by using the sudo make command in the ndiswrapper folder. I end up with this:
gigi@gigi:~/ndiswrapper-1.47$ sudo make
Password:
make -C driver
make[1]: Entering directory `/home/gigi/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/gigi/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/gigi/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/gigi/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/gigi/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/gigi/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/gigi/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/gigi/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/gigi/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:160: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:217: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:217: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:221: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:222: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:224: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:232: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:232: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:249: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:249: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:255: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:267: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:271: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:280: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8216;strcasecmp&#8217;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:318: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:344: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:346: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:348: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:355: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:355: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:357: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: In function &#8216;get_device&#8217;:
loadndisdriver.c:367: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:370: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:370: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:373: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:374: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8216;snprintf&#8217;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8216;snprintf&#8217;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:367: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_device&#8217;:
loadndisdriver.c:419: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:419: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:423: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:426: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:427: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:429: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:464: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:464: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:473: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:473: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:483: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:489: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:489: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:489: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:490: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:495: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:511: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:511: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:511: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:513: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:517: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:527: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:542: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:549: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:590: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/gigi/ndiswrapper-1.47/utils'
make: *** [all] Error 2


What am I doing wrong?

---

### Post by Paris Heng on 2007-09-11
What kind of WiFi that u use? USB tye? PCMCIA?

---

### Post by bardoksan on 2007-09-11
The card is a D-Link (DWL-G510 Rev. A) PCI. (marvel 8k51 chipset)

Other posts mention that build-essential is needed, but that won't install right either. It says that libc6-dev, g++ and a few others are needed as dependancies but are not available from my source (Kubuntu 7.04 DVD 32bit).

I'm trying not to have to use that other computers LAN port, so I don't have to disable it later. So my only sources are the install DVD and files that I can download to a memory stick using this box then transfer to the problem box.

---

### Post by kevdog on 2007-09-11
You need to install the linux headers -- that is what you are missing

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```

---

### Post by westyonfire on 2007-12-06
Just a massive thank you from me. I'm a linux newbie and have been trying to get my wireless card (Netgear WG311v3) working for weeks, and this finally got it working. so thanks again.

---

### Post by kolibri on 2008-02-28
this is great- I had these errors as well.  What does it mean to have to install the linux headers, and why isn't it done automatically as part of the ubuntu install?

---

### Post by kevdog on 2008-02-28
I'm not sure why the header files are not installed by default.  If you ever have done any C programming they are files needed for linking functions defined in other files -- specifically files located in the kernel.  Why don't you post a question in the forum asking why the linux header files are not installed by default?

---

