---
title: "Configuring Broadcom on Edgy Eft"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by Rudy507 on 2006-10-31
Hey guys,
I'm using instructions [here]("http://ubuntuforums.org/showthread.php?t=286924") and [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") to install ndiswrapper with the hopes of getting my Dell Wireless 1370 WLAN Mini-PCI Card (made by Broadcom) working. 

I just installed Edgy Eft fresh today with the hopes of it automatically getting my card to work, but alas! Still the same 'ol problem. (I never actually got it working on Dapper... although I didn't put TOO much effort into it).

So I did the following:

Step 1: I downloaded ndiswrapper 1.28.
Step 2: Tar -xzvf ndiswrapper
Step 3: Make Uninstall (just to make sure)
-- sure enough, I had to go in and remove a ndsiwrapper directory in /lib/modules/...
Step 4 (once it was completely uninstalled): Make
-- And THIS is where I began running into problems. By the way, I'm of course running the default kernel. Would the kernel version have anything to do with these errors?

Here's the output. Thanks for any help you can give.
> 
root@smoothstoneserv:/manual_install/ndiswrapper-1.28# make
make -C driver
make[1]: Entering directory `/manual_install/ndiswrapper-1.28/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/manual_install/ndiswrapper-1.28/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/manual_install/ndiswrapper-1.28/driver'
make -C utils
make[1]: Entering directory `/manual_install/ndiswrapper-1.28/utils'
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
loadndisdriver.c:219: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:219: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:221: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:223: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:224: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:226: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:232: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:234: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:234: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:234: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:252: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:254: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:262: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:264: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:270: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:270: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:274: warning: implicit declaration of function ‘memset’
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:275: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:283: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:283: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:285: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function ‘stat’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:320: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:321: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:285: warning: unused variable ‘statbuf’
loadndisdriver.c:347: error: expected expression before ‘struct’
loadndisdriver.c:349: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:351: warning: implicit declaration of function ‘free’
loadndisdriver.c:358: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:360: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:371: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:374: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:377: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:378: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:380: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:380: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:403: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:371: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:415: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:415: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:420: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:422: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:425: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:430: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:431: error: dereferencing pointer to incomplete type
loadndisdriver.c:432: error: dereferencing pointer to incomplete type
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:444: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:461: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:461: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:469: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:469: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:470: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:470: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:480: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:485: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:486: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:486: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:486: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:488: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:493: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:509: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:509: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:509: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:513: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:515: warning: implicit declaration of function ‘printf’
loadndisdriver.c:515: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:525: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:540: warning: implicit declaration of function ‘atof’
loadndisdriver.c:547: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:554: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:588: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/manual_install/ndiswrapper-1.28/utils'
make: *** [all] Error 2


---

### Post by LinLenLap on 2006-10-31
Try this thread:

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)

My lspci | grep Broadcom\ Corporation returns:

01:02.0 Network controller: Broadcom Corporation Dell Wireless 1470 DualBand WLAN (rev 02)

Also, I have my router set to 'G' only, not mixed. Some people think that makes a difference.

Oh and because you've already tried ndiswrapper you might have to blacklist it. Look elsewhere for that.

I know its not exactly your card, but mine works and is reported as a Dell.

Best,

LLL

---

