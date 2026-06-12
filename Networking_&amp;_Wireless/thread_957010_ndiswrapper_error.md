---
title: "ndiswrapper error"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by .vinsai. on 2008-10-23
I've been trying to get my Dell truemobile 1300 card, and I've been playing with ndiswrapper all night trying to get it to work.  When I unzip the tarball and use the 'make' command inside the freshly unzipped directory, here's the response I get, in full.

```
coffee@coffee-laptop:~/Documents/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/coffee/Documents/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/coffee/Documents/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/coffee/Documents/ndiswrapper-1.53/driver/built-in.o
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/crt_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/hal_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/ndis_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/ntoskernel_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/ntoskernel_io_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/rtl_exports.h
  MKEXPORT /home/coffee/Documents/ndiswrapper-1.53/driver/usb_exports.h
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/crt.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/hal.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/iw_ndis.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/loader.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/ndis.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/ntoskernel.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/ntoskernel_io.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/pe_linker.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/pnp.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/proc.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/rtl.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/wrapmem.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/wrapndis.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/wrapper.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/usb.o
  CC [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/divdi3.o
  LD [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/coffee/Documents/ndiswrapper-1.53/driver/ndiswrapper.mod.o
  LD [M]  /home/coffee/Documents/ndiswrapper-1.53/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/home/coffee/Documents/ndiswrapper-1.53/driver'
make -C utils
make[1]: Entering directory `/home/coffee/Documents/ndiswrapper-1.53/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:28: error: expected specifier-qualifier-list before ‘size_t’
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
make[1]: Leaving directory `/home/coffee/Documents/ndiswrapper-1.53/utils'
make: *** [all] Error 2
```

I also tried installing from 'sudo apt-get install ndiswrapper-common' which seemed to work, but tells me it needs utils to load >.< .  I'm still fairly new to linux so I might be missing something fairly simple.  Can anyone point me in the right direction here?

---

### Post by cariboo on 2008-10-23
The files you need are on the LiveCD that you installed Ubuntu with, They are located in /pool/main/n. You should also install ndisgtk, 
this is a gui interface for ndiswrapper and makes setting things up a lot easier.

Jim

---

### Post by Ayuthia on 2008-10-24
The package that you are missing to compile ndiswrapper is build-essential.  The package that you need with ndiswrapper-common is ndiswrapper-utils-1.9.  Both of those packages are on the live CD.  As cariboo907 mentioned, ndisgtk is a helpful tool that is also on the CD.

I would recommend going with cariboo907's option only because the packages on the CD will always be updated automatically where the compiled version will have to be recompiled every time that there is a kernel change.

---

### Post by .vinsai. on 2008-10-25
Thanks for the replies, not gonna have access to my lappy tonight but I'll post results.

---

### Post by .vinsai. on 2008-10-25
Found all the files on the cd, but I'm having trouble actually installing them.  I've completely extracted all of the zips and have tried using the commands './configure', 'make' and 'make install' in every conceivable directory, but I still can't get the files to install :confused:


**edit, I'm a double posting ****tard, whoops. :X

Well, I installed them using the package manager (right click is the cure-all) and now I've got everything working and installed, I pointed it to the .inf file for my dell truemobile 1300 and....still nothing.  No lights coming on or anything.  Am I stewpid?  Don't answer that...but feel free to answer the other question, feels like I'm aaaaalmost there.

---

### Post by edyeeh on 2008-10-25
try posting to this thread dedicated to ndiswrapper. pytheas solved my problems there :)

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by Ayuthia on 2008-10-25
Can you post the results of:
```
lspci -nn
lshw -C network
ndiswrapper -l
```
The first command will help us see what card you are using, the second will let us know what driver it is trying to use, and the third will tell us if the driver is present and if there are any possible conflicting modules.

---

### Post by .vinsai. on 2008-10-26
That ndsiwrapper thread is really helpful, it seems like my driver is the wrong one for my architecture.  Here's the output of those commands:

lspci -nn returns:


```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
```


lshw -C network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:1d:59:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:c6:24:a6:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
```

It looks like the drivers aren't loading, the thread on ndiswrapper suggests using 'lsmod | grep ndis' to check.  When I type that I get 
```
ndiswrapper     192920   0
usbcore         146028   6 usb_storage, libusual, ndiswrapper, ehci_hcd, uhci_hcd
cd
```

The thread never specifies what to do if you do get a response to that command, only how to deal with it if it returns nothing >.<

---

### Post by Ayuthia on 2008-10-26
> **.vinsai. said:**
> That ndsiwrapper thread is really helpful, it seems like my driver is the wrong one for my architecture.  Here's the output of those commands:

lspci -nn returns:


```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
```


lshw -C network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:1d:59:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:10:c6:24:a6:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

ndiswrapper -l
```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)
```

It seems to be acting like I'm using the wrong chipset driver for it, but I got the driver directly from the dell website so I can only assume the chipset is correct....

It looks like you have not blacklisted all the wireless modules.  Try the following (will only work for this session):
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo modprobe b44
```

If that works, please post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -e b4 -e ssb -e ndis -e bcm -e wl
cat /etc/modules|grep -e b4 -e ssb -e ndis -e bcm -e wl
```
This will help us figure out what you need to add/remove to make your wireless work on reboot.

---

### Post by .vinsai. on 2008-10-26
the first command didn't work, it tells me that ssb is in use.  I ran the other two commands but the card still comes up as disabled when I run lshw -C network.

**Edit:
My LAN connection is gone now :-\ .  lshw -C network lists my ethernet controller UNCLAIMED.  How do I switch that back?

---

### Post by eternal_sage on 2008-10-26
same problem here.

---

### Post by Ayuthia on 2008-10-26
> **.vinsai. said:**
> the first command didn't work, it tells me that ssb is in use.  I ran the other two commands but the card still comes up as disabled when I run lshw -C network.

**Edit:
My LAN connection is gone now :-\ .  lshw -C network lists my ethernet controller UNCLAIMED.  How do I switch that back?

Sorry about that.  I forgot that you have the b43legacy module.  Try this:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
```
I forgot to have you restart the networking.  When I had you remove the b44 module and load it back, it turned off your wired connection.

---

### Post by .vinsai. on 2008-10-26
lol thats cool I figured out how to turn it back on.  I removed everything and reactivated ndiswrapper and b44 and restarted and now I'm online!  Here's the results of the cat search you posted, I couldn't figure out what to do with this information:

cat /etc/modprobe.d/blacklist
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

The second returned nothing.  Thanks so much for all the help!

---

### Post by Ayuthia on 2008-10-26
> **.vinsai. said:**
> lol thats cool I figured out how to turn it back on.  I removed everything and reactivated ndiswrapper and b44 and restarted and now I'm online!  Here's the results of the cat search you posted, I couldn't figure out what to do with this information:

cat /etc/modprobe.d/blacklist
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

The second returned nothing.  Thanks so much for all the help!

The first file prevents certain modules from loading.  The second file loads modules after the kernel modules have been loaded.  Your results show that you have not blacklisted the b43, ssb, and wl modules and have not loaded the ndiswrapper module.  Here is what you need to add (slightly modified from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3)):
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 

echo ndiswrapper | sudo tee -a /etc/modules
```
The one is a script that will be run when the ndiswrapper module is loaded.  It will remove all the conflicting modules, load ndiswrapper, then load the b44 module.  The second command adds the ndiswrapper module to /etc/modules so that it will be loaded after the kernel has loaded all of the modules it needed.

Hope this helps!

---

### Post by .vinsai. on 2008-10-28
That took care of everything, thanks a bunch!

You still having problems sage?

---

### Post by eternal_sage on 2008-10-28
yes, my wife's computer responds to the fix (modprobe etc etc) but it will not accept the script to make the fix permanent. i'm not sure whats up with that.

and to add to the trouble, my laptop, which has been running intrepid fine for the last two months yesterday got an update which has made its wireless card stop working. this is starting to get upsetting since i don't even need ndiswrapper to get my card in the laptop working, it used to work out of the box, but now will not even show me the possible list of networks to connect to. the system is registering the wireless card's existence, it just can't use it. if i cannot get this fixed in short order, i will be going back to hardy until all the bugs that apparently have been added in the last few days are worked out.

---

### Post by Ayuthia on 2008-10-28
> **eternal_sage said:**
> yes, my wife's computer responds to the fix (modprobe etc etc) but it will not accept the script to make the fix permanent. i'm not sure whats up with that.

and to add to the trouble, my laptop, which has been running intrepid fine for the last two months yesterday got an update which has made its wireless card stop working. this is starting to get upsetting since i don't even need ndiswrapper to get my card in the laptop working, it used to work out of the box, but now will not even show me the possible list of networks to connect to. the system is registering the wireless card's existence, it just can't use it. if i cannot get this fixed in short order, i will be going back to hardy until all the bugs that apparently have been added in the last few days are worked out.

If your wife's computer is using ndiswrapper, can you post the results of:
```
/etc/modprobe.d/ndiswrapper
```I just want to verify that the information in there is correct.  Also, have you tried any other scripts to fix it?  Some guides have people create things in /etc/init.d and some in /etc/rc.local.  That could also be causing the problem.

Out of curiosity, what card do you have?  There seems to be a lot of problems lately with either the atheros, intel, and wl drivers.  It is either in Hardy with the 2.6.24-21 or else it is in Intrepid with the 2.6.27-7.

---

### Post by eternal_sage on 2008-10-29
i'll check that out

both laptops are using intrepid right now, neither have been tinkered with other than what is in this thread (and the other thread), and i'm going to go out on a limb and say they are both intel, although i will check for sure and post back.

again thanks for everything so far.

---

