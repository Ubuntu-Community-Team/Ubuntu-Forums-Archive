---
title: "wireless on Compaq Presario v3000 and Edgy"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by quantumscape on 2007-01-27
Hello,

I just installed Edgy on my Compaq Presario v3000z and I'm trying to follow the instructions on this webpage to get the wirelss connection to work: [http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html](http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html)

But, I'm running into a problem and would really like someone to help me. 

You see, when I get to the step "sudo ndiswrapper -i bcmwl5.inf" I got the error that "sudo: ndiswrapper: command not found."

So, i checked back to the output when I did the "make & sudo make install" command and I noticed that I did get a bunch of errors. Here's everything that was on my terminal concerning that, (but the top was cut off by the terminal).

 >  CC [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/quantumscape/Desktop/working/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/utils'
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
make[1]: Leaving directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/utils'
make: *** [all] Error 2
quantumscape@quantumscape:~/Desktop/working/ndiswrapper-1.34$ sudo make install
make -C driver install
make[1]: Entering directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/quantumscape/Desktop/working/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-10-generic/misc
/sbin/depmod -a 2.6.17-10-generic -b /
make[1]: Leaving directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/driver'
make -C utils install
make[1]: Entering directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/utils'
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
make[1]: Leaving directory `/home/quantumscape/Desktop/working/ndiswrapper-1.34/utils'
make: *** [install] Error 2


Alright, so the sort of it is that I need help figuring out what happened. I think it could be because we're using two different versions of linux or because I don't have the latest development packages. (Which I wasn't sure how to download.) 

So, thanks for reading this! I hope you can help.
-QS

---

### Post by quantumscape on 2007-01-27
Update: I figured out how to get the linux-kernel-devel from the synapse package manager. I went through the rest of the instructions aok. But, when I get to iwconfig, I still can't use my wireless network for some reason. When type in "iwconfig" I get the following output:
> eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Even when I do set the ESSID I still can't log on. Does anyone know what I should do?

Thanks!

---

### Post by xxzeenoxx on 2007-02-01
I have an R3000z and this is what i do and it never fails:

Since you already have ndiswrapper installed, try uninstalling it from the Synaptic Package Manager.

Next follow the steps for the BCM43xx chipset:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)


After you have done that, run the following commands in a terminal:


sudo apt-get install network-manager-gnome

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Reboot

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.


I hope this helps......

---

### Post by FrodoB on 2007-02-01
Take a look at this guide and follow it to the point that you have ndiswrapper built.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)

---

