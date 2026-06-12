---
title: "Problem installing gyachi-1.2.7.tar.gz &amp; Cheese 2.30.1"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Zirthang on 2010-06-16
Hi! I got some problems while I tried to install GyachI & Cheese. I want to use yahoo chat client for video chat. While I tried to install I got some error:

[HTML]
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... ./configure: line 12500: intltool-update: command not found
 found
configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
zirthang@zirthang-laptop:~/cheese-2.30.1$ make
make: *** No targets specified and no makefile found.  Stop.
zirthang@zirthang-laptop:~/cheese-2.30.1$ sudo make
[sudo] password for zirthang: 
make: *** No targets specified and no makefile found.  Stop.
zirthang@zirthang-laptop:~/cheese-2.30.1$ sudo make
make: *** No targets specified and no makefile found.  Stop.
zirthang@zirthang-laptop:~/cheese-2.30.1$ make install
make: *** No rule to make target `install'.  Stop.
[/HTML]


I use ubuntu 10.04 & I am a absolute newbie in Ubuntu but Love it Because It has some wonderful features. Please help. I installed GyachI v1.1.48 with .deb package. but These are .tar.gz so don't know how to configure or install manually.

---

### Post by proggy on 2010-06-16
If you want the latest gyachi go here [https://launchpad.net/~baudm/+archive/ppa](https://launchpad.net/~baudm/+archive/ppa)

---

