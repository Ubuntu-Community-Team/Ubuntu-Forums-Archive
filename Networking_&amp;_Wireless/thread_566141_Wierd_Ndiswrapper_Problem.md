---
title: "Wierd Ndiswrapper Problem"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by zedi123 on 2007-10-03
Hi
Iv got a bit of a problem here...

Basically i had to reinstall Feisty and all my settings were wiped :(
I had my wireless all set up and working but now whenever i try to install Ndiswrapper it keeps giving me errors, it never did this before.
Can someone help??

heres what the terminal tells me:

> zahid@Griever:~/ndiswrapper-1.48$ sudo make
make -C driver
make[1]: Entering directory `/home/zahid/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/zahid/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
 LD      /home/zahid/ndiswrapper-1.48/driver/built-in.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/crt.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/hal.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/iw_ndis.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/loader.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/ndis.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/ntoskernel.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/ntoskernel_io.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/pe_linker.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/pnp.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/proc.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/rtl.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/wrapmem.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/wrapndis.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/wrapper.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/usb.o
 CC [M]  /home/zahid/ndiswrapper-1.48/driver/divdi3.o
 LD [M]  /home/zahid/ndiswrapper-1.48/driver/ndiswrapper.o
 Building modules, stage 2.
 MODPOST 1 modules
 CC      /home/zahid/ndiswrapper-1.48/driver/ndiswrapper.mod.o
 LD [M]  /home/zahid/ndiswrapper-1.48/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/zahid/ndiswrapper-1.48/driver'
make -C utils
make[1]: Entering directory `/home/zahid/ndiswrapper-1.48/utils'
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
../driver/loader.h:24: error: expected specifier-qualifier-list before 
loadndisdriver.c: In function :
loadndisdriver.c:67: error:  undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected  before 
loadndisdriver.c:68: error:  undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of  isnbasenameopenO_RDONLYsyslogLOG_KERNLOG_INFOstrerrorerrnoEINVALfstatclosesizemmapPROT_READMAP_PRIVATEMAP_FAILEDstrncpystrncpystruct load_driver_filesizestruct load_driver_filedatastatbufparse_setting_lineisspacestrchrstrchrNULLLOG_KERNLOG_INFOEINVALstrlenstrlenread_conf_filestatbuft known
loadndisdriver.c:151: error:  undeclared (first use in this function)
loadndisdriver.c:151: error:  undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function 
loadndisdriver.c:158: error:  undeclared (first use in this function)
loadndisdriver.c:158: error:  undeclared (first use in this function)
loadndisdriver.c:158: error:  undeclared (first use in this function)
loadndisdriver.c:160: error:  undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function 
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:178: warning: implicit declaration of function 
loadndisdriver.c:178: error:  undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function 
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:205: warning: implicit declaration of function 
loadndisdriver.c:150: warning: unused variable 
loadndisdriver.c: In function :
loadndisdriver.c:217: error:  undeclared (first use in this function)
loadndisdriver.c:217: error:  undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function 
loadndisdriver.c:221: warning: implicit declaration of function 
loadndisdriver.c:222: error:  undeclared (first use in this function)
loadndisdriver.c:224: error:  undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:232: warning: implicit declaration of function 
loadndisdriver.c:232: warning: implicit declaration of function 
loadndisdriver.c:232: error: expected expression before 
loadndisdriver.c: In function :
loadndisdriver.c:249: error:  undeclared (first use in this function)
loadndisdriver.c:249: error:  undeclared (first use in this function)
loadndisdriver.c:251: error:  undeclared (first use in this function)
loadndisdriver.c:255: error:  undeclared (first use in this function)
loadndisdriver.c:255: error:  undeclared (first use in this function)
loadndisdriver.c:257: error:  undeclared (first use in this function)
loadndisdriver.c:259: error:  undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function 
loadndisdriver.c:267: warning: implicit declaration of function 
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:271: warning: implicit declaration of function 
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:280: warning: implicit declaration of function 
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of  isnstatS_ISREGstrlenstrcasecmpstrcpystrcpystruct load_driver_filesizestruct load_driver_filedatastatbufstructclosedirfreemunmapstruct load_driver_filedatastruct load_driver_filesizestruct load_driver_filedatastruct load_driver_filesizeget_devicestatbuft known
loadndisdriver.c:370: error:  undeclared (first use in this function)
loadndisdriver.c:370: error:  undeclared (first use in this function)
loadndisdriver.c:373: error:  undeclared (first use in this function)
loadndisdriver.c:374: error:  undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function 
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:367: warning: unused variable 
loadndisdriver.c: In function :
loadndisdriver.c:419: error:  undeclared (first use in this function)
loadndisdriver.c:419: error:  undeclared (first use in this function)
loadndisdriver.c:423: error:  undeclared (first use in this function)
loadndisdriver.c:423: error:  undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:426: error:  undeclared (first use in this function)
loadndisdriver.c:427: error:  undeclared (first use in this function)
loadndisdriver.c:429: error:  undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before 
loadndisdriver.c: In function :
loadndisdriver.c:464: error:  undeclared (first use in this function)
loadndisdriver.c:464: error:  undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function 
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:473: warning: implicit declaration of function 
loadndisdriver.c:473: error:  undeclared (first use in this function)
loadndisdriver.c:483: error:  undeclared (first use in this function)
loadndisdriver.c:483: error:  undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function 
loadndisdriver.c:489: warning: implicit declaration of function 
loadndisdriver.c:489: error:  undeclared (first use in this function)
loadndisdriver.c:489: error:  undeclared (first use in this function)
loadndisdriver.c:490: error:  undeclared (first use in this function)
loadndisdriver.c:495: error:  undeclared (first use in this function)
loadndisdriver.c: In function :
loadndisdriver.c:511: warning: implicit declaration of function 
loadndisdriver.c:511: error:  undeclared (first use in this function)
loadndisdriver.c:511: error:  undeclared (first use in this function)
loadndisdriver.c:511: error:  undeclared (first use in this function)
loadndisdriver.c:511: error:  undeclared (first use in this function)
loadndisdriver.c:513: error:  undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function 
loadndisdriver.c:517: warning: implicit declaration of function 
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:527: warning: implicit declaration of function 
loadndisdriver.c:542: warning: implicit declaration of function 
loadndisdriver.c:549: warning: implicit declaration of function 
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function 
loadndisdriver.c:590: warning: implicit declaration of function 
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/zahid/ndiswrapper-1.48/utils'
make: *** [all] Error 2

---

### Post by dmizer on 2007-10-03
well, first of all, you appear to be missing a lot of dependencies.

second of all, is it absolutely necessary for you to be using the ndiswrapper from source?  you should try the package available in synaptic before you resort to installing from source.

---

### Post by kevdog on 2007-10-03
Your missing the linux header files.

Do the following assuming you have an ethernet connection:

sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by zedi123 on 2007-10-03
Thanx guys i'll try ur suggestions, anything to get it working again.
Btw i would love to use the synaptic version of ndiswrapper but its only version 1.38 and for some reason it doesn't work with my driver.

---

### Post by kevdog on 2007-10-03
Build from source.

Try this for a reference.  Instructions how to compile from source are at the bottom:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

If you know how to use svn, I would do that also.

---

