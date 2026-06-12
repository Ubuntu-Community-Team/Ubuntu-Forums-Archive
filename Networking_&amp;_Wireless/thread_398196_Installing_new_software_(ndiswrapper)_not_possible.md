---
title: "Installing new software (ndiswrapper) not possible!"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by niko@andolini on 2007-03-31
i would like to get my wireless pci card working with ndiswrapper. so far i haven't even managed to install ndiswrapper. i also tried to install other software such as g++4 but all i got back were error messages. it seems my system doesn't want to compile correctly at all.

when i tried it with ndiswrapper, after unpacking i typed as root 'make', terminal answered:

root@andolini:~/ndiswrapper-1.39# make
make -C driver
make[1]: Entering directory 

`/home/nike/ndiswrapper-1.39/driver'
make -C 

/lib/modules/2.6.17-10-generic/build 

SUBDIRS=/home/nike/ndiswrapper-1.39/driver
make[2]: Entering directory 

`/usr/src/linux-headers-2.6.17-10-generic'
  LD      

/home/nike/ndiswrapper-1.39/driver/built-in.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/crt.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/hal.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/iw_ndis.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/loader.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/ndis.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/ntoskernel.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/ntoskernel_io.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/pe_linker.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/pnp.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/proc.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/rtl.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/wrapmem.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/wrapndis.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/wrapper.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/usb.o
  CC [M]  

/home/nike/ndiswrapper-1.39/driver/divdi3.o
  LD [M]  

/home/nike/ndiswrapper-1.39/driver/ndiswrapper.o
  Building modules, stage 2.
  

MODPOST
  CC      /home/nike/ndiswrapper-1.39/driver/ndiswrapper.mod.o
  LD [M]  

/home/nike/ndiswrapper-1.39/driver/ndiswrapper.ko
make[2]: Leaving directory 

`/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory 

`/home/nike/ndiswrapper-1.39/driver'
make -C utils
make[1]: Entering directory 

`/home/nike/ndiswrapper-1.39/utils'
gcc -g -Wall -I../driver -o loadndisdriver 

loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or 

directory
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
In file 

included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
          

       from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
              

   from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No 

such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or 

directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file 

included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected 

specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function 

‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this 

function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported 

only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: 

error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: 

error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: 

implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: 

initialization makes pointer from integer without a cast
------
loadndisdriver.c:491: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:496: error: ‘O_RDONLY’ undeclared (first use in this 

function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:512: warning: 

implicit declaration of function ‘openlog’
loadndisdriver.c:512: error: 

‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:512: 

error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:512: 

error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:512: 

error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:514: 

error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:516: 

warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:518: 

warning: implicit declaration of function ‘printf’
loadndisdriver.c:518: 

warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:528: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:543: warning: implicit declaration of function ‘atof’
loadndisdriver.c:550: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:557: warning: incompatible implicit declaration of built-in 

function ‘sscanf’
loadndisdriver.c:591: warning: implicit declaration of 

function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving 

directory `/home/nike/ndiswrapper-1.39/utils'
make: *** [all] Error 2

----------------------------------

please help

---

### Post by Jussi Kukkonen on 2007-03-31
Are you sure you need to compile things? Ubuntu has a pretty good selection of software available as binaries. Ndiswrapper seems to be available.

You might want to look for howtos in the forum or the wiki -- I'm quite sure they exist.

---

### Post by ntraft on 2008-03-11
Well ndiswrapper 1.38 ships with Ubuntu 7.04. You just need to install the utils package (ndiswrapper-utils-1.9), but the driver is there. Unfortunately, it's way behind the current driver version 1.48 that you can get if you compile from sources.

A lot of people have found that to get reliable wireless with ndiswrapper they had to use a more recent driver version than what's in Feisty.

I get the same EXACT problem when I try to compile.  I am running Ubuntu 7.10 x86, and I am trying to find a solution right now.  I will post if I find one.

---

