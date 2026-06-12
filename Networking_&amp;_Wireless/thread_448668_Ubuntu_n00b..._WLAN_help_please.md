---
title: "Ubuntu n00b... WLAN help please"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by dpernal on 2007-05-19
while i am a relative n00b to ubuntu, i've played with other distros before.  here's my dilemma:

trying to get my WLAN card installed.  it's a dell wireless draft 1500n in an inspiron e1405.  have found at least four separate how-tos, and when following the directions to the "T," i still get nothing.  i've installed the bcm43xx drivers, ndiswrapper and dell drivers, etc.  still nothing.  my wi-fi light isn't even on.  i've gone into the bios and disabled the f2 hot-key, made sure that wi-fi is enabled by default, etc.  everything's fine, i think.  here's the latest slap in the face when trying to run "sudo make" in the ndiswrapper-1.34 dir after running "sudo make distclean."
```

dpernal@dpernal-laptop:/home/WLAN/ndiswrapper-1.34$ sudo make
make -C driver
make[1]: Entering directory `/home/WLAN/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/WLAN/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/WLAN/ndiswrapper-1.34/driver/built-in.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/crt.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/hal.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/iw_ndis.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/loader.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/ndis.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/ntoskernel.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/ntoskernel_io.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/pe_linker.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/pnp.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/proc.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/rtl.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/wrapmem.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/WLAN/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/WLAN/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/WLAN/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/WLAN/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/WLAN/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/WLAN/ndiswrapper-1.34/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/WLAN/ndiswrapper-1.34/utils'
make: *** [all] Error 2

```

apologies for the long code paste, but maybe someone can get something out of it to help me.

thanks in advance,
dp

---

### Post by dpernal on 2007-05-19
right.... ubuntu 7.04 (the feisty fawn)

---

