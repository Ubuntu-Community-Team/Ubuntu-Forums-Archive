---
title: "no makefile grub conf"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by kaoru666 on 2009-03-21
I am trying to install grubconf  [http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/) a gui for editing the grub configuration file but when I run the "make" command I just get - no makefile found* The ./configure completes sucessfully. Any ideas?
heres the output

ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ ./configure
loading cache ./config.cache
checking for non-GNU ld... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0... ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ sudo apt-get libgnomeui-2.0
E: Invalid operation libgnomeui-2.0
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ sudo apt-get libgnomeui-2.0 gtk+-2.0
E: Invalid operation libgnomeui-2.0
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ sudo apt-get gtk+-2.0
E: Invalid operation gtk+-2.0
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ clear

ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ ./configure
loading cache ./config.cache
checking for non-GNU ld... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0... ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$

---

### Post by taurus on 2009-03-21
You need to include the install with apt-get.

```
sudo apt-get **install** package_name
```

---

### Post by kaoru666 on 2009-03-21
it's not in synaptic I am trying to compile it

---

### Post by sandyd on 2009-03-21
hes trying to compile a program from source, not installing it from the resipostries

@OP. can you navigate to that directory where you typed ./configure and type in
```

ls

```P.S.

put your result in [code] tags
its much cleaner and easier to read.

---

### Post by kaoru666 on 2009-03-21
```
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ ls
ABOUT-NLS     config.h.in   grubconf.8           macros         README
acconfig.h    config.log    grubconf.desktop.in  Makefile.am    src
acinclude.m4  config.sub    help                 Makefile.in    stamp-h.in
aclocal.m4    configure     include              missing        TODO
AUTHORS       configure.in  INSTALL              mkinstalldirs  xmldocs.make
ChangeLog     conftest      install-sh           NEWS
confdefs.h    conftest.c    intl                 omf.make
config.cache  conftest.o    libtool              pixmaps
config.guess  COPYING       ltmain.sh            po

```

---

### Post by sandyd on 2009-03-21
run
```

sudo ./install-sh

```

i encountered the same problem as you on some other source code.
spent like 30 minutes mucking around wondering why it wouldn't work and finally found out there was a install script

lame...

---

### Post by kaoru666 on 2009-03-21
unfortunately no luck

```
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ sudo ./install-sh
install:	no input file specified

```

---

### Post by taurus on 2009-03-21
> ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ **sudo apt-get libgnomeui-2.0 gtk+-2.0**
E: Invalid operation libgnomeui-2.0
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ **sudo apt-get gtk+-2.0**
E: Invalid operation gtk+-2.0
What's wrong with those two commands?

The answer is you forgot to include the _install_ in there if you want to install a package from the repos.

---

### Post by kaoru666 on 2009-03-21
okay thanks I got a little further this time the configure finshed and I have a make file but when I run the make command I end up getting a compilation error ```
ka0ru@ka0ruth3hakz0r:~/Desktop/grubconf-0.5.1$ sudo make
make  all-recursive
make[1]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1'
Making all in intl
make[2]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/intl'
Making all in po
make[2]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/po'
Making all in include
make[2]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/include'
Making all in macros
make[2]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/macros'
Making all in src
make[2]: Entering directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12      -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -Wmissing-prototypes 	 -O1 	 -g -c main.c
main.c: In function ‘main’:
main.c:129: warning: ignoring return value of ‘getcwd’, declared with attribute warn_unused_result
In function ‘open’,
    inlined from ‘main’ at main.c:137:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ka0ru/.local/share/Trash/files/grubconf-0.5.1'
make: *** [all-recursive-am] Error 2

```

---

