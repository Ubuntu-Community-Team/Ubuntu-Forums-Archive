---
title: "Trouble compiling ndiswrapper 1.27 in breezy"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by gregpavy on 2006-10-26
Hey all, 

Quick question, big error, and probably a simple fix. Unfortunately, I can't figure it out. Any ideas?

In an attempt to compile ndiswrapper 1.27, I have downloaded the current kernel headers (uname -r: 2.6.12-10). After moving to the ndiswrapper1.27 directory, I give it the following command:

sudo make KBUILD="/usr/src/linux- headers-2.6.12-10-386"

And get a lot of nastiness midway through. I'm cutting and pasting the nastiness for ya:

make -C driver
make[1]: Entering directory `/home/greg/Desktop/ndiswrapper-1.27/driver'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/home/greg/Desktop/ndiswrapper-1.27/driver
make[2]: Entering directory `/usr/src/linux- headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/home/greg/Desktop/ndiswrapper-1.27/driver'
make -C utils
make[1]: Entering directory `/home/greg/Desktop/ndiswrapper-1.27/utils'
gcc-3.4 -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: stdlib.h: No such file or directory
loadndisdriver.c :16:19: stdio.h: No such file or directory
loadndisdriver.c:17:19: errno.h: No such file or directory
loadndisdriver.c:18:20: string.h: No such file or directory
loadndisdriver.c:19:20: libgen.h: No such file or directory
loadndisdriver.c:21:22: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: sys/types.h: No such file or directory
loadndisdriver.c:24:23: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: unistd.h: No such file or directory
loadndisdriver.c:27:19: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/limits.h:122:61: limits.h: No such file or directory
loadndisdriver.c:29:19: ctype.h: No such file or directory
loadndisdriver.c :30:20: dirent.h: No such file or directory
loadndisdriver.c:31:20: syslog.h: No such file or directory
loadndisdriver.c:34:25: linux/major.h: No such file or directory
loadndisdriver.c:35:25: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: parse error before "size_t"
../driver/loader.h:24: warning: no semicolon at end of struct or union
../driver/loader.h:26: error: parse error before '}' token
../driver/loader.h:52: error: field `sys_files' has incomplete type
../driver/loader.h:56: error: field `bin_files' has incomplete type
loadndisdriver.c: In function `load_file':
loadndisdriver.c:67: error: `size_t' undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: parse error before "size"
loadndisdriver.c :68: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of 'statbuf' isn't known
loadndisdriver.c:71: warning: implicit declaration of function `basename'
loadndisdriver.c :71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function `open'
loadndisdriver.c:73: error: `O_RDONLY' undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function `syslog'
loadndisdriver.c:75: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:75: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function `strerror'
loadndisdriver.c:75: error: `errno' undeclared (first use in this function)
loadndisdriver.c:76: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function `fstat'
loadndisdriver.c:81: warning: implicit declaration of function `close'
loadndisdriver.c:84: error: `size' undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function `mmap'
loadndisdriver.c:86: error: `PROT_READ' undeclared (first use in this function)
loadndisdriver.c:86: error: `MAP_PRIVATE' undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: `MAP_FAILED' undeclared (first use in this function)loadndisdriver.c:93: warning: implicit declaration of function `strncpy'
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:93: error: dereferencing pointer to incomplete type
loadndisdriver.c:94: error: dereferencing pointer to incomplete type
loadndisdriver.c :94: error: dereferencing pointer to incomplete type
loadndisdriver.c:95: error: dereferencing pointer to incomplete type
loadndisdriver.c:96: error: dereferencing pointer to incomplete type
loadndisdriver.c:69: warning: unused variable `statbuf'
loadndisdriver.c: In function `parse_setting_line':
loadndisdriver.c:109: warning: implicit declaration of function `isspace'
loadndisdriver.c:115: warning: implicit declaration of function `strchr'
loadndisdriver.c :115: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:117: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:117: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:118: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function `strlen'
loadndisdriver.c: In function `read_conf_file':
loadndisdriver.c :150: error: storage size of 'statbuf' isn't known
loadndisdriver.c:151: error: `FILE' undeclared (first use in this function)
loadndisdriver.c:151: error: `config' undeclared (first use in this function)
loadndisdriver.c :157: warning: implicit declaration of function `lstat'
loadndisdriver.c:158: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:158: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:158: error: `errno' undeclared (first use in this function)
loadndisdriver.c:160: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function `sscanf'
loadndisdriver.c:179: warning: implicit declaration of function `fopen'
loadndisdriver.c:179: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function `fgets'
loadndisdriver.c:206: warning: implicit declaration of function `fclose'
loadndisdriver.c:150: warning: unused variable `statbuf'
loadndisdriver.c: In function `load_bin_file':
loadndisdriver.c:215: error: storage size of 'driver_file' isn't known
loadndisdriver.c:219: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:219: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:221: warning: implicit declaration of function `tolower'
loadndisdriver.c:223: warning: implicit declaration of function `chdir'
loadndisdriver.c:224: error: `errno' undeclared (first use in this function)
loadndisdriver.c:226: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:234: warning: implicit declaration of function `ioctl'
loadndisdriver.c:234: warning: implicit declaration of function `_IOW'
loadndisdriver.c:234: error: parse error before "struct"
loadndisdriver.c:215: warning: unused variable `driver_file'
loadndisdriver.c: At top level:
loadndisdriver.c:238: error: parse error before "return"
loadndisdriver.c: In function `load_driver':
loadndisdriver.c :252: error: `DIR' undeclared (first use in this function)
loadndisdriver.c:252: error: `driver_dir' undeclared (first use in this function)
loadndisdriver.c:254: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:258: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:258: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:260: error: `errno' undeclared (first use in this function)
loadndisdriver.c:262: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:264: warning: implicit declaration of function `opendir'
loadndisdriver.c:270: warning: implicit declaration of function `malloc'
loadndisdriver.c:274: warning: implicit declaration of function `memset'
loadndisdriver.c:283: warning: implicit declaration of function `readdir'
loadndisdriver.c:283: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:285: error: storage size of 'statbuf' isn't known
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function `stat'
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function `S_ISREG'
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: warning: implicit declaration of function `strcasecmp'
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c :316: warning: implicit declaration of function `strcpy'
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c :285: warning: unused variable `statbuf'
loadndisdriver.c:347: error: parse error before "struct"
loadndisdriver.c:349: warning: implicit declaration of function `closedir'
loadndisdriver.c:351: warning: implicit declaration of function `free'
loadndisdriver.c:358: warning: implicit declaration of function `munmap'
loadndisdriver.c: In function `get_device':
loadndisdriver.c:371: error: storage size of 'statbuf' isn't known
loadndisdriver.c:374: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:374: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:377: error: `errno' undeclared (first use in this function)
loadndisdriver.c:378: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:380: warning: implicit declaration of function `snprintf'
loadndisdriver.c:371: warning: unused variable `statbuf'
loadndisdriver.c: In function `load_device':
loadndisdriver.c:415: error: `DIR' undeclared (first use in this function)
loadndisdriver.c:415: error: `dir' undeclared (first use in this function)
loadndisdriver.c:419: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:419: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:422: error: `errno' undeclared (first use in this function)
loadndisdriver.c:423: error: `EINVAL' undeclared (first use in this function)
loadndisdriver.c:425: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:430: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:431: error: dereferencing pointer to incomplete type
loadndisdriver.c:432: error: dereferencing pointer to incomplete type
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:444: error: parse error before "struct"
loadndisdriver.c: In function `get_ioctl_device':
loadndisdriver.c:461: error: `FILE' undeclared (first use in this function)
loadndisdriver.c:461: error: `proc_misc' undeclared (first use in this function)loadndisdriver.c:469: warning: implicit declaration of function `strstr'
loadndisdriver.c:470: warning: implicit declaration of function `strtol'
loadndisdriver.c:470: error: `NULL' undeclared (first use in this function)
loadndisdriver.c:480: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:480: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:485: warning: implicit declaration of function `unlink'
loadndisdriver.c:486: warning: implicit declaration of function `mknod'
loadndisdriver.c:486: error: `S_IFCHR' undeclared (first use in this function)
loadndisdriver.c:486: error: `MISC_MAJOR' undeclared (first use in this function)
loadndisdriver.c:488: error: `errno' undeclared (first use in this function)
loadndisdriver.c:493: error: `O_RDONLY' undeclared (first use in this function)
loadndisdriver.c: In function `main':
loadndisdriver.c:509: warning: implicit declaration of function `openlog'
loadndisdriver.c:509: error: `LOG_PERROR' undeclared (first use in this function)
loadndisdriver.c :509: error: `LOG_CONS' undeclared (first use in this function)
loadndisdriver.c:509: error: `LOG_KERN' undeclared (first use in this function)
loadndisdriver.c:509: error: `LOG_DEBUG' undeclared (first use in this function)loadndisdriver.c:511: error: `LOG_INFO' undeclared (first use in this function)
loadndisdriver.c:513: warning: implicit declaration of function `strncmp'
loadndisdriver.c:515: warning: implicit declaration of function `printf'
loadndisdriver.c:525: warning: implicit declaration of function `atoi'
loadndisdriver.c:540: warning: implicit declaration of function `atof'
loadndisdriver.c:547: warning: implicit declaration of function `strcmp'
loadndisdriver.c:588: warning: implicit declaration of function `closelog'
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/greg/Desktop/ndiswrapper-1.27/utils'
make: *** [all] Error 2


Okay, so it's prolly something really stupid, and those lines at the top

"
oadndisdriver.c:15:20: stdlib.h: No such file or directory
loadndisdriver.c:16:19: stdio.h: No such file or directory
loadndisdriver.c:17:19: errno.h: No such file or directory
loadndisdriver.c:18:20: string.h: No such file or directory
loadndisdriver.c:19:20: libgen.h: No such file or directory
loadndisdriver.c:21:22: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: sys/types.h: No such file or directory
loadndisdriver.c:24:23: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: unistd.h: No such file or directory
loadndisdriver.c:27:19: fcntl.h: No such file or directory....
etc, etc

Indicate it's looking and not finding some config setting, right? But what?

Any help is appreciated. Thanks!

---

### Post by vectormax on 2006-11-02
Make sure you have "libc6-dev" package installed.  I got it off Synaptic, as I was having the same problem compiling "ndiswrapper-1.28" for "Edgy"

vectormax

---

### Post by Subw00fer on 2006-12-17
> **vectormax said:**
> Make sure you have "libc6-dev" package installed.  I got it off Synaptic, as I was having the same problem compiling "ndiswrapper-1.28" for "Edgy"

vectormax

I am receiving the same exact error but I don't think that I can run Synaptic since I don't have an internet connection.  How do I fix this error without internet?

---

