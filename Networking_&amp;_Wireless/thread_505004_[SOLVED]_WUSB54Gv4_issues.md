---
title: "[SOLVED] WUSB54Gv4 issues"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-07-19
I have been trying with no success to get my WUSB54Gv4 Linksys wireless card working. I just reinstalled Feisty and it still doesn't work out of the box like the WifiDocs says it does. I have just downloaded and tried to install ndiswrapper-1.47 and I keep getting the same error. Here is the output (I apologize for the length):

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
kelly@kelly-desktop:~$ cd Desktop 
kelly@kelly-desktop:~/Desktop$ ls 
ndiswrapper-1.47.tar.gz 
kelly@kelly-desktop:~/Desktop$ tar -zxvf ndiswrapper-1.47.tar.gz 
ndiswrapper-1.47/ 
ndiswrapper-1.47/AUTHORS 
ndiswrapper-1.47/ChangeLog 
ndiswrapper-1.47/INSTALL 
ndiswrapper-1.47/Makefile 
ndiswrapper-1.47/README 
ndiswrapper-1.47/ndiswrapper.spec 
ndiswrapper-1.47/ndiswrapper.8 
ndiswrapper-1.47/loadndisdriver.8 
ndiswrapper-1.47/utils/ 
ndiswrapper-1.47/utils/Makefile 
ndiswrapper-1.47/utils/ndiswrapper 
ndiswrapper-1.47/utils/loadndisdriver.c 
ndiswrapper-1.47/utils/ndiswrapper-buginfo 
ndiswrapper-1.47/driver/ 
ndiswrapper-1.47/driver/divdi3.c 
ndiswrapper-1.47/driver/hal.c 
ndiswrapper-1.47/driver/iw_ndis.c 
ndiswrapper-1.47/driver/iw_ndis.h 
ndiswrapper-1.47/driver/loader.c 
ndiswrapper-1.47/driver/loader.h 
ndiswrapper-1.47/driver/longlong.h 
ndiswrapper-1.47/driver/Makefile 
ndiswrapper-1.47/driver/crt.c 
ndiswrapper-1.47/driver/ndis.c 
ndiswrapper-1.47/driver/ndis.h 
ndiswrapper-1.47/driver/ndiswrapper.h 
ndiswrapper-1.47/driver/ntoskernel.c 
ndiswrapper-1.47/driver/ntoskernel.h 
ndiswrapper-1.47/driver/ntoskernel_io.c 
ndiswrapper-1.47/driver/pe_linker.c 
ndiswrapper-1.47/driver/pe_linker.h 
ndiswrapper-1.47/driver/pnp.c 
ndiswrapper-1.47/driver/pnp.h 
ndiswrapper-1.47/driver/proc.c 
ndiswrapper-1.47/driver/rtl.c 
ndiswrapper-1.47/driver/usb.c 
ndiswrapper-1.47/driver/usb.h 
ndiswrapper-1.47/driver/winnt_types.h 
ndiswrapper-1.47/driver/workqueue.c 
ndiswrapper-1.47/driver/wrapmem.h 
ndiswrapper-1.47/driver/wrapmem.c 
ndiswrapper-1.47/driver/wrapper.c 
ndiswrapper-1.47/driver/wrapndis.h 
ndiswrapper-1.47/driver/wrapndis.c 
ndiswrapper-1.47/driver/lin2win.h 
ndiswrapper-1.47/driver/win2lin_stubs.S 
kelly@kelly-desktop:~/Desktop$ cd ndiswrapper-1.47 
kelly@kelly-desktop:~/Desktop/ndiswrapper-1.47$ ls 
AUTHORS    driver   loadndisdriver.8  ndiswrapper.8     README 
ChangeLog  INSTALL  Makefile          ndiswrapper.spec  utils 
kelly@kelly-desktop:~/Desktop/ndiswrapper-1.47$ make distclean 
make -C driver clean 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \ 
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \ 
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers 
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
make -C utils clean 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
rm -f *~ *.o loadndisdriver 
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
rm -f *~ 
rm -fr ndiswrapper-1.47 ndiswrapper-1.47.tar.gz patch-stamp 
make -C driver distclean 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \ 
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \ 
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers 
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o 
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
make -C utils distclean 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
rm -f *~ *.o loadndisdriver 
rm -f .\#* 
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
rm -f .\#* 
kelly@kelly-desktop:~/Desktop/ndiswrapper-1.47$ make 
make -C driver 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/kelly/Desktop/ndiswrapper-1.47/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic' 
  LD      /home/kelly/Desktop/ndiswrapper-1.47/driver/built-in.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/crt.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/hal.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/iw_ndis.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/loader.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/ndis.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/ntoskernel.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/ntoskernel_io.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/pe_linker.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/pnp.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/proc.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/rtl.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/wrapmem.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/wrapndis.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/wrapper.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/usb.o 
  CC [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/divdi3.o 
  LD [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/ndiswrapper.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/kelly/Desktop/ndiswrapper-1.47/driver/ndiswrapper.mod.o 
  LD [M]  /home/kelly/Desktop/ndiswrapper-1.47/driver/ndiswrapper.ko 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic' 
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/driver' 
make -C utils 
make[1]: Entering directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
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
make[1]: Leaving directory `/home/kelly/Desktop/ndiswrapper-1.47/utils' 
make: *** [all] Error 2 
kelly@kelly-desktop:~/Desktop/ndiswrapper-1.47$  


Please help, I need someone that I can troubleshoot this issue with step by step until it is resolved. I would be very grateful!

---

### Post by JawsThemeSwimming428 on 2007-07-22
Problem solved: See [http://ubuntuforums.org/showthread.php?t=489800](http://ubuntuforums.org/showthread.php?t=489800)

---

