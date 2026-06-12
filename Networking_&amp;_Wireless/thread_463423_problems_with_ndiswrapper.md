---
title: "problems with ndiswrapper"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Zboarda on 2007-06-03
Hi there, I'm new to Ubuntu and Linux and I'm trying oh so desperately to get on the internet. I'm wanting to use a Netgear WG111v2 usb dongle. I've tried ndiswrapper but it don't work...I've tried the make uninstall and make and make install and then I tried the ndiswrapper command and it don't work. This is probably an obvious issue but I would appreciate any help. Thanks. 

Zboarda

---

### Post by gunbladeiv on 2007-06-03
what version of ubuntu are you using?

if it is feisty then try changing to Dapper. Ive tried ndiswrapper on feisty but it wont work.

---

### Post by snowdude on 2007-06-03
what error messages do you get when you try to make it? do you have gcc installed? For some reason for me when I installed ubuntu gcc didn't come with it. to add it just type "sudo apt-get install build-essential" and then try compiling ndiswrapper.

---

### Post by gunbladeiv on 2007-06-04
> **snowdude said:**
> what error messages do you get when you try to make it? do you have gcc installed? For some reason for me when I installed ubuntu gcc didn't come with it. to add it just type "sudo apt-get install build-essential" and then try compiling ndiswrapper.

yup i have installed ndiswrapper with feisty and yes i do have build-essential packages.  I had no problem when compiling the tarball of ndiswrapper.  but when i install the windows driver it just wont work.  I did the same command like i did with dapper, it just wont work with feisty.

---

### Post by kevdog on 2007-06-04
if you type ndiswrapper -v what does it tell you.  Something tells me you might have multiple versions of ndiswrapper installed in the kernel.

Where did you obtain the ndiswrapper tarball?? Directly from the ndiswrapper sourceforge website???

Simply compiling the tarball is not enough.  You need to remove the old ndiswrapper from the kernel:
sudo modprobe -r ndiswrapper.

Remove any traces of ndiswrapper from the system and current kernel.
Install the compiled ndiswrapper with current driver.
Reinsert ndiswrapper into the kernel:
sudo depmod -a
sudo modprobe ndiswrapper.

Then it might work.

---

### Post by Zboarda on 2007-06-04
> what version of ubuntu are you using?
I am using ubuntu 6.1. I was using 7.04, btw is this the fiesty and dapper business?
> do you have gcc installed?
No, at least I didn't put it on.
> if you type ndiswrapper -v what does it tell you.
It says bad command, command doesn't exist or whatever.

Maybe I can add to this. When I do make and make install it gives a load of messages and some errors.
Here is a list of the errors and what I input in the terminal.
```

tim@tim-desktop:~$ sudo modprobe -r ndiswrapper
Password:
tim@tim-desktop:~$ sudo modprobe -r ndiswrapper
tim@tim-desktop:~$ sudo pepmod -a
sudo: pepmod: command not found
tim@tim-desktop:~$ sudo modprobe ndiswrapper
tim@tim-desktop:~$ sudo depmod -a
tim@tim-desktop:~$ sudo modprobe ndiswrapper
tim@tim-desktop:~$ ndiswrapper
bash: ndiswrapper: command not found
tim@tim-desktop:~$ cd ~/Desktop
tim@tim-desktop:~/Desktop$ cd ndiswrapper-*
tim@tim-desktop:~/Desktop/ndiswrapper-1.45$ make
make -C driver
make[1]: Entering directory `/home/tim/Desktop/ndiswrapper-1.45/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/tim/Desktop/ndiswrapper-1.45/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/tim/Desktop/ndiswrapper-1.45/driver'
make -C utils
make[1]: Entering directory `/home/tim/Desktop/ndiswrapper-1.45/utils'
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
make[1]: Leaving directory `/home/tim/Desktop/ndiswrapper-1.45/utils'
make: *** [all] Error 2
tim@tim-desktop:~/Desktop/ndiswrapper-1.45$ make install
make -C driver install
make[1]: Entering directory `/home/tim/Desktop/ndiswrapper-1.45/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/tim/Desktop/ndiswrapper-1.45/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
mkdir: cannot create directory `/lib/modules/2.6.17-10-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tim/Desktop/ndiswrapper-1.45/driver'
make: *** [install] Error 2

```

---

### Post by kevdog on 2007-06-04
2 issues as you can probably guess:

1. It doesnt look like you have ndiswrapper installed (you probably know this).  Just ensure its not hiding somewhere
sudo updatedb
locate ndiswrapper

If you could post the output of the above along with the kernel version you are using:
uame -r

2. You obviously do not have the required c libraries installed in order to compile the tarball -- hence all the errors.  I take you you have installed build-essential package.  I believe you probably need to verify the installation or install the glib libraries.  Probably the best thing to do is to go into synaptic and search for libglib and then download the appropriate libraries.  You might also want to install svn.

Of course if you cant connect to the internet, step #2 might be difficult.

---

### Post by Zboarda on 2007-06-04
Ok, I've had a thought. What is strange is that ubuntu already picks up the netgear usb dongle up. Is there a way I can configure it to what channel it transmits? I have tried dhcp because my win xp pc is finding the internet by automatically find settings. Then I tried a static ip address and input my stuff but the internet still doesn't work...

Here is the output anyway:
```

tim@tim-desktop:~$ sudo updatedb
Password:
tim@tim-desktop:~$ locate ndiswrapper
/var/log/autondiswrapper.log
/home/tim/Desktop/ndiswrapper-1.45
/home/tim/Desktop/ndiswrapper-1.45/AUTHORS
/home/tim/Desktop/ndiswrapper-1.45/ChangeLog
/home/tim/Desktop/ndiswrapper-1.45/INSTALL
/home/tim/Desktop/ndiswrapper-1.45/Makefile
/home/tim/Desktop/ndiswrapper-1.45/README
/home/tim/Desktop/ndiswrapper-1.45/ndiswrapper.spec
/home/tim/Desktop/ndiswrapper-1.45/ndiswrapper.8
/home/tim/Desktop/ndiswrapper-1.45/loadndisdriver.8
/home/tim/Desktop/ndiswrapper-1.45/utils
/home/tim/Desktop/ndiswrapper-1.45/utils/Makefile
/home/tim/Desktop/ndiswrapper-1.45/utils/ndiswrapper
/home/tim/Desktop/ndiswrapper-1.45/utils/loadndisdriver.c
/home/tim/Desktop/ndiswrapper-1.45/utils/ndiswrapper-buginfo
/home/tim/Desktop/ndiswrapper-1.45/driver
/home/tim/Desktop/ndiswrapper-1.45/driver/divdi3.c
/home/tim/Desktop/ndiswrapper-1.45/driver/hal.c
/home/tim/Desktop/ndiswrapper-1.45/driver/iw_ndis.c
/home/tim/Desktop/ndiswrapper-1.45/driver/iw_ndis.h
/home/tim/Desktop/ndiswrapper-1.45/driver/loader.c
/home/tim/Desktop/ndiswrapper-1.45/driver/loader.h
/home/tim/Desktop/ndiswrapper-1.45/driver/longlong.h
/home/tim/Desktop/ndiswrapper-1.45/driver/Makefile
/home/tim/Desktop/ndiswrapper-1.45/driver/crt.c
/home/tim/Desktop/ndiswrapper-1.45/driver/ndis.c
/home/tim/Desktop/ndiswrapper-1.45/driver/ndis.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ndiswrapper.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel.c
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel_io.c
/home/tim/Desktop/ndiswrapper-1.45/driver/pe_linker.c
/home/tim/Desktop/ndiswrapper-1.45/driver/pe_linker.h
/home/tim/Desktop/ndiswrapper-1.45/driver/pnp.c
/home/tim/Desktop/ndiswrapper-1.45/driver/pnp.h
/home/tim/Desktop/ndiswrapper-1.45/driver/proc.c
/home/tim/Desktop/ndiswrapper-1.45/driver/rtl.c
/home/tim/Desktop/ndiswrapper-1.45/driver/usb.c
/home/tim/Desktop/ndiswrapper-1.45/driver/usb.h
/home/tim/Desktop/ndiswrapper-1.45/driver/winnt_types.h
/home/tim/Desktop/ndiswrapper-1.45/driver/workqueue.c
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapmem.h
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapmem.c
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapper.c
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapndis.h
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapndis.c
/home/tim/Desktop/ndiswrapper-1.45/driver/lin2win.h
/home/tim/Desktop/ndiswrapper-1.45/driver/win2lin_stubs.S
/home/tim/Desktop/ndiswrapper-1.45/driver/crt_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ndis_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/hal_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel_io_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/rtl_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/usb_exports.h
/home/tim/Desktop/ndiswrapper-1.45/driver/.tmp_versions
/home/tim/Desktop/ndiswrapper-1.45/driver/.tmp_versions/ndiswrapper.mod
/home/tim/Desktop/ndiswrapper-1.45/driver/built-in.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.built-in.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel.o
/home/tim/Desktop/ndiswrapper-1.45/driver/crt.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.crt.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/loader.o
/home/tim/Desktop/ndiswrapper-1.45/driver/hal.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.hal.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.ndis.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/iw_ndis.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.iw_ndis.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.loader.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/ndis.o
/home/tim/Desktop/ndiswrapper-1.45/driver/ndiswrapper.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.ntoskernel.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.ntoskernel_io.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/ntoskernel_io.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.pe_linker.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/pe_linker.o
/home/tim/Desktop/ndiswrapper-1.45/driver/proc.o
/home/tim/Desktop/ndiswrapper-1.45/driver/pnp.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.pnp.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.proc.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/divdi3.o
/home/tim/Desktop/ndiswrapper-1.45/driver/rtl.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.rtl.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapndis.o
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapmem.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.wrapmem.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.wrapndis.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/usb.o
/home/tim/Desktop/ndiswrapper-1.45/driver/wrapper.o
/home/tim/Desktop/ndiswrapper-1.45/driver/.wrapper.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.usb.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.divdi3.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.ndiswrapper.o.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/ndiswrapper.mod.c
/home/tim/Desktop/ndiswrapper-1.45/driver/Modules.symvers
/home/tim/Desktop/ndiswrapper-1.45/driver/ndiswrapper.mod.o
/home/tim/Desktop/ndiswrapper-1.45/driver/ndiswrapper.ko
/home/tim/Desktop/ndiswrapper-1.45/driver/.ndiswrapper.ko.cmd
/home/tim/Desktop/ndiswrapper-1.45/driver/.ndiswrapper.mod.o.cmd
/home/tim/Desktop/ndiswrapper-1.45.tar.gz
/home/tim/Desktop/autondiswrapper-1.45a.tar.bz2
/home/tim/Desktop/autondiswrapper
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/loadndisdriver.8
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/Makefile
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/ndiswrapper.spec
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/ChangeLog
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/utils
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/utils/loadndisdriver.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/utils/ndiswrapper-buginfo
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/utils/Makefile
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/utils/ndiswrapper
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/ndiswrapper.8
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/pe_linker.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/hal.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/loader.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/wrapndis.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ntoskernel.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/wrapper.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/lin2win.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/Makefile
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/wrapndis.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/crt.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/rtl_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/iw_ndis.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/workqueue.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/pe_linker.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ntoskernel_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/crt_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/longlong.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/iw_ndis.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/loader.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/rtl.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/divdi3.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/pnp.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ntoskernel_io_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ndis.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/usb.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ntoskernel_io.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ndis_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/wrapmem.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/winnt_types.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/usb_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/built-in.o
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/wrapmem.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/hal_exports.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ndiswrapper.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/pnp.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/usb.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ntoskernel.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/ndis.h
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/win2lin_stubs.S
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/driver/proc.c
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/README
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/AUTHORS
/home/tim/Desktop/autondiswrapper/ndiswrapper-1.45/INSTALL
/home/tim/Desktop/autondiswrapper/get-bcm43xx.sh
/home/tim/Desktop/autondiswrapper/auto-ndiswrapper.sh
/home/tim/Desktop/autondiswrapper/driver
/home/tim/Desktop/autondiswrapper/driver/netwpn11.inf
/home/tim/Desktop/autondiswrapper/driver/WPN111.sys
/home/tim/Desktop/autondiswrapper/LICENSE-NDISWRAPPER
/home/tim/Desktop/autondiswrapper/INSTALL
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/src/linux-headers-2.6.17-10/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.17-10/drivers/net/ndiswrapper/Makefile
/usr/src/linux-headers-2.6.17-10/include/config/ndiswrapper.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/ndiswrapper
/usr/src/linux-headers-2.6.17-10-generic/include/config/ndiswrapper/module.h
tim@tim-desktop:~$ uname -r
2.6.17-10-generic

```

also where can I get the neccesary files and libraries for ndiswrapper to work?

---

### Post by eiskalt on 2007-06-04
you gotta remember that ndiswrapper is a "wrapper", not a magic bullet.  You will need a driver file usually from windowz, which ndiswrapper will install.  
This tutorial was pretty good, check the /etc/iftab file as it says in this tutorial.
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Yes, this is for a broadcom, but it should get you on the right path.

---

### Post by gunbladeiv on 2007-06-04
if you want to install ndiwrapper why dont you just do it by apt-get?

try this command in the terminal.

apt-get update
apt-get install ndiswrapper

i think this might work for you.
this command will automatically install ndiswrapper to your linux.

---

### Post by kevdog on 2007-06-05
You obviously dont have ndiswrapper installed.

2 options

Easiest:
1. Install pre-compiled package
     If you dont have internet connection (Side rant -- thats what gets me about these forums, users tell you to download files from internet, although that is the problem, you cant.  There is no internet connection! Hence the help trying to set up the connection), install ndiswrapper from ubuntu cd.  Place cd in drive then:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper

2. Compile and install from source.
   If you have the build-essential package installed I think this will work.  Go to the directory where you unzipped the tarball.  Then run make distclean and make. As root, run make install.

Either way should install the ndiswrapper package!

---

### Post by Zboarda on 2007-06-09
Yay I have ndiswrapper installed and the driver is installed but...there is no ip addy for the card or any packets sent or recieved...
Please help...again.
Thanks

---

### Post by kevdog on 2007-06-09
Sorry I havent checked this post in a couple of days.  From what I saw with the output of your locate ndiswrapper package is that you downloaded and unzipped the package, but I dont believe you actually installed the package!

Unzipping the tarball is not the same as installing it.  The tarball is simply source files.  These source files need to be compiled and then installed.  When you tried this before (refer to post a few back), by issuing the make command (make=compile), you got a bunch of errors stating xxxx.h not found.  What this means is that you do not have the header files installed for your kernel.  Without the header files, you can not compile or make ndiswrapper.

If at any time you type:
ndiswrapper -v
and the result is file is not found, ndiswrapper has not been installed.

Possible solutions for you.
1. If you want to compile and install from source:
a. Find out what kernel you have installed: uname -r
A name with long number should be returned
Using the above, you will need to find the header package for the kernel you have.  
After installation of header package you should be able to compile and install ndiswrapper

2. If you just want to download the precompiled ndiswrapper package:
sudo aptitude update
sudo aptitude install ndiswrapper

3. Ndiswrapper is simply a wrapper - that wraps a windows driver -- making it appear as a linux driver. (Ok maybe a simplification, but this analogy works).  You need to find the appropriate windows driver for your card, or specifically the chipset contained inside your card.  You should know the brand and model of your card.  To find the chipset, type:
lspci
and look for the network controller line.
Using the above information, go to the ndiswrapper sourceforge website: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
and then find your card on the list.  Using the information, download the driver they recommend.

4. Whether you compiled and installed ndiswrapper from source or using aptitude - everything should be the same right now.
a. Make sure ndiswrapper is installed: ndiswrapper -v
b. Go into the directory where your driver you downloaded in step #3 is located.  There should be at least two files in the directory a .sys file and .inf file.
c. Uninstall any previous ndiswrapper installation:
sudo modprobe -r ndiswrapper
sudo modprobe -r bcm43xx
d. Then issue following command making sure there are no errors:
sudo depmod -a
e. Wrap ndiswrapper around windows driver:
ndiswrapper -i xxxxx.inf
Substitute the name of the .inf file above.
f. Install ndiswrapper package into kernel:
sudo modprobe ndiswrapper

By default ndiswrapper assumes your interface name is wlan0.  I dont know if this is the case for you or not. To see what your wireless connection interface name is, look at the /etc/iftab file.
more /etc/iftab

If the line states anything except wlan0 (like eth0 or something) edit the file:
gksu gedit /etc/iftab
and substitute wlan0 in place of eth0 (or whatever).

Then you need to modify your /etc/network/interfaces file:
gksu gedit /etc/network/interfaces

Again substitute or type wlan0 anywhere you see eth0 (or whatever the old interface name was).

g. Make sure ndiswrapper starts at boot
sudo ndiswrapper -a

Reboot computer.  Even after reboot, you might need to restart networking services:
sudo /etc/init.d/networking restart

Hopefully now you can connect.

---

