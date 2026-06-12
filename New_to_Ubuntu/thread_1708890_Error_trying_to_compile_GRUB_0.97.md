---
title: "Error trying to compile GRUB 0.97"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by vmsda on 2011-03-17
For an educational exercise, I download the source code from GRUB 0.97 and try to compile it. However, the ./configure command produces an error. Please have a look:

```
vasco@vasco-laptop:~/project$ ls
grub-0.97  grub-0.97.tar.gz
vasco@vasco-laptop:~/project$ cd grub-0.97/
vasco@vasco-laptop:~/project/grub-0.97$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc -mcpu=i386
checking for gcc... (cached) gcc -mcpu=i386
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc -mcpu=i386 accepts -g... yes
checking for gcc -mcpu=i386 option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc -mcpu=i386... gcc3
checking dependency style of gcc -mcpu=i386... (cached) gcc3
checking for ranlib... ranlib
checking whether optimization for size works... yes
checking whether gcc has -fno-stack-protector... yes
checking whether -Wundef works... yes
checking whether -falign-loops works... yes
checking for objcopy... objcopy
checking if C symbols get an underscore after compilation... no
checking whether objcopy works for absolute addresses... no
configure: error: GRUB requires a working absolute objcopy; upgrade your binutils
vasco@vasco-laptop:~/project/grub-0.97$ 

```

Help would be greatly appreciated. Thank in advance.

---

### Post by oldos2er on 2011-03-17
Did you check the README and/or INSTALL files for a list of dependencies?

---

### Post by vmsda on 2011-03-17
> **oldos2er said:**
> Did you check the README and/or INSTALL files for a list of dependencies?

The INSTALL file lists binutils 2.9.1.0.23. The installed version in my Ubuntu is 2.20.1-3ubuntu7.1. So it seemed to me that there would be no problems, but that is obviously not the case.

Thanks for the help.

---

