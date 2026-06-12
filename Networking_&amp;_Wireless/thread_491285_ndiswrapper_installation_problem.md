---
title: "ndiswrapper installation problem"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-07-03
I'm trying to install ndiswrapper-1.47 from the tar.gz file which I downloaded. Using make disclean, make and make install, everything seems to go ok, though there are a couple of error messages along the way. When I try ndiswraper -v, I get the error message "ndiswrapper not installed"
When I look in filebrowser, the ndiswrapper folder is present, along with what looks like all the required files.
I've repeated the process several times, once with version 1-42, always with the same result.
Can someone out there tell me where I'm going wrong??

---

### Post by kevdog on 2007-07-03
Here is the correct syntax

make distclean
make
sudo make install

---

### Post by glendavee on 2007-07-03
Sorry - there was a typo in my first post. I did use the correct syntax, ie 
make distclean
make
sudo make install

---

### Post by kevdog on 2007-07-03
You have to tell me then what the error messages were.  There has got to be a reason those last three statements are not working.  I get messages, but no errors when executing the three statements.

---

### Post by glendavee on 2007-07-03
I've cut and pasted most of the error output, as follows. Sorry for the size of the post - hope you can make sense out of it, I can't :

LD [M]  /home/david/ndiswrapper-1.47/driver/ndiswrapper.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/david/ndiswrapper-1.47/driver/ndiswrapper.mod.o 
  LD [M]  /home/david/ndiswrapper-1.47/driver/ndiswrapper.ko 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
make[1]: Leaving directory `/home/david/ndiswrapper-1.47/driver' 
make -C utils 
make[1]: Entering directory `/home/david/ndiswrapper-1.47/utils' 
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
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’ 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’ 
loadndisdriver.c:150: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’ 
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function) 
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’ 
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’ 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’ 
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’ 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’ 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:284: error: dereferencing pointer to incomplete type 
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’ 
loadndisdriver.c:287: error: dereferencing pointer to incomplete type 
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’ 
loadndisdriver.c:289: error: dereferencing pointer to incomplete type 
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c:294: error: dereferencing pointer to incomplete type 
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’ 
loadndisdriver.c:296: error: dereferencing pointer to incomplete type 
loadndisdriver.c:299: error: dereferencing pointer to incomplete type 
loadndisdriver.c:302: error: dereferencing pointer to incomplete type 
loadndisdriver.c:303: error: dereferencing pointer to incomplete type 
loadndisdriver.c:305: error: dereferencing pointer to incomplete type 
loadndisdriver.c:311: error: dereferencing pointer to incomplete type 
loadndisdriver.c:312: error: dereferencing pointer to incomplete type 
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’ 
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’ 
loadndisdriver.c:314: error: dereferencing pointer to incomplete type 
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:321: error: dereferencing pointer to incomplete type 
loadndisdriver.c:282: warning: unused variable ‘statbuf’ 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’ 
loadndisdriver.c:348: warning: implicit declaration of function ‘free’ 
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c: In function ‘get_device’: 
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’ 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:367: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:435: error: dereferencing pointer to incomplete type 
loadndisdriver.c:436: error: dereferencing pointer to incomplete type 
loadndisdriver.c:439: error: dereferencing pointer to incomplete type 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function) 
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’ 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’ 
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’ 
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function) 
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c: In function ‘main’: 
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function) 
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’ 
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’ 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’ 
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’ 
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’ 
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’ 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/home/david/ndiswrapper-1.47/utils' 
make: *** [all] Error 2 
david@david-laptop:~/ndiswrapper-1.47$ su make install 
Unknown id: make 
david@david-laptop:~/ndiswrapper-1.47$ su 
Password: 
root@david-laptop:/home/david/ndiswrapper-1.47# make install 
make -C driver install 
make[1]: Entering directory `/home/david/ndiswrapper-1.47/driver' 
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/david/ndiswrapper-1.47/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
echo /lib/modules/2.6.20-15-generic/misc 
/lib/modules/2.6.20-15-generic/misc 
mkdir -p /lib/modules/2.6.20-15-generic/misc 
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc 
/sbin/depmod -a 2.6.20-15-generic -b / 
make[1]: Leaving directory `/home/david/ndiswrapper-1.47/driver' 
make -C utils install 
make[1]: Entering directory `/home/david/ndiswrapper-1.47/utils' 
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
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’ 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’ 
loadndisdriver.c:150: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’ 
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’ 
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function) 
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’ 
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’ 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’ 
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’ 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’ 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:284: error: dereferencing pointer to incomplete type 
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’ 
loadndisdriver.c:287: error: dereferencing pointer to incomplete type 
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’ 
loadndisdriver.c:289: error: dereferencing pointer to incomplete type 
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’ 
loadndisdriver.c:294: error: dereferencing pointer to incomplete type 
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’ 
loadndisdriver.c:296: error: dereferencing pointer to incomplete type 
loadndisdriver.c:299: error: dereferencing pointer to incomplete type 
loadndisdriver.c:302: error: dereferencing pointer to incomplete type 
loadndisdriver.c:303: error: dereferencing pointer to incomplete type 
loadndisdriver.c:305: error: dereferencing pointer to incomplete type 
loadndisdriver.c:311: error: dereferencing pointer to incomplete type 
loadndisdriver.c:312: error: dereferencing pointer to incomplete type 
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’ 
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’ 
loadndisdriver.c:314: error: dereferencing pointer to incomplete type 
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:321: error: dereferencing pointer to incomplete type 
loadndisdriver.c:282: warning: unused variable ‘statbuf’ 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’ 
loadndisdriver.c:348: warning: implicit declaration of function ‘free’ 
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’ 
loadndisdriver.c: In function ‘get_device’: 
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known 
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’ 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’ 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’ 
loadndisdriver.c:367: warning: unused variable ‘statbuf’ 
loadndisdriver.c: In function ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function) 
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function) 
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast 
loadndisdriver.c:435: error: dereferencing pointer to incomplete type 
loadndisdriver.c:436: error: dereferencing pointer to incomplete type 
loadndisdriver.c:439: error: dereferencing pointer to incomplete type 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: In function ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function) 
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function) 
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’ 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’ 
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’ 
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function) 
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function) 
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function) 
loadndisdriver.c: In function ‘main’: 
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function) 
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function) 
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’ 
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’ 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’ 
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’ 
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’ 
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’ 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’ 
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: Leaving directory `/home/david/ndiswrapper-1.47/utils' 
make: *** [install] Error 2 
root@david-laptop:/home/david/ndiswrapper-1.47# exit 
exit 
david@david-laptop:~/ndiswrapper-1.47$ ndiswrapper -v 
The program 'ndiswrapper' is currently not installed.  You can install it by typing: 
sudo apt-get install ndiswrapper-common 
bash: ndiswrapper: command not found 
david@david-laptop:~/ndiswrapper-1.47$

---

### Post by kevdog on 2007-07-03
Just a hunch...

If you have an internet (ie wired) connection skip to step #4.
1. Insert ubuntu installation cd into drive and wait to become ready
At command line type:
2. sudo apt-cdrom add
3. sudo aptitude update
4. sudo aptitude install build-essential

Then go ahead with the 3 former commands, disclean,make,make install

Post if there are any more errors.

---

### Post by glendavee on 2007-07-03
No, I don't have internet access on this machine. Only way is via a wireless router, hence the need to get ndiswrapper sorted out.

---

### Post by kevdog on 2007-07-03
Ok, since you dont have internet access, start with step#1 and move forward

---

### Post by glendavee on 2007-07-04
Problem solved. I managed to rig a wired internet connection, and via this downloaded updates and the graphical ngistgk package. Using the graphical interface, managed to get ndiswrapper installed.
Thanks for the help.
Next problem will be installing the driver........

---

