---
title: "Trying to install partimage"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-01
So I didn't find anything by searching,
and like usual the irc is ignoring me.

I've done apt-get build-dep
Output is as follows currently;
```
aji@aij-dtp:~/partimage-0.6.7$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for gawk... (cached) mawk
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for pthread_create in -lpthread... yes
checking for BZ2_bzopen in -lbz2... yes
checking for newtCenteredWindow in -lnewt... yes
checking for gzwrite in -lz... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for strings.h... (cached) yes
checking limit.h usability... no
checking limit.h presence... no
checking for limit.h... no
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking shadow.h usability... yes
checking shadow.h presence... yes
checking for shadow.h... yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether setpgrp takes no argument... yes
checking for getwd... yes
checking for strerror... yes
checking for strdup... yes
checking for atoll... yes
checking for strtoll... yes
checking for setpgid... yes
checking for fstat64... yes
checking for fstatfs64... yes
checking for open64... yes
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long int... yes
checking size of long int... 8
checking for unsigned long long... yes
checking size of unsigned long long... 8
checking for ANSI C header files... (cached) yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for getopt.h... (cached) yes
checking for sys/types.h... (cached) yes

checking for openssl... /usr/bin/openssl
configure: checking  for SSL Library and Header files ... ...
checking "for rsa.h crypto.h x509.h pem.h ssl.h err.h"... (/usr/include/openssl) yes 
checking for CRYPTO_lock in -lcrypto... yes
checking for SSL_CTX_new in -lssl... yes
checking for crypt in -lcrypt... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/shared/Makefile
config.status: creating src/shared/pathnames.h
config.status: creating src/client/Makefile
config.status: creating src/client/fs/Makefile
config.status: creating src/server/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands


``````
aji@aij-dtp:~/partimage-0.6.7$ 
aji@aij-dtp:~/partimage-0.6.7$ sudo make
make  all-recursive
make[1]: Entering directory `/home/aji/partimage-0.6.7'
Making all in m4
make[2]: Entering directory `/home/aji/partimage-0.6.7/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aji/partimage-0.6.7/m4'
Making all in po
make[2]: Entering directory `/home/aji/partimage-0.6.7/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aji/partimage-0.6.7/po'
Making all in src
make[2]: Entering directory `/home/aji/partimage-0.6.7/src'
Making all in shared
make[3]: Entering directory `/home/aji/partimage-0.6.7/src/shared'
g++ -DHAVE_CONFIG_H -DLOCALEDIR=\"/usr/local/share/locale\" -D_REENTRANT -D_FILE_OFFSET_BITS=64 -I. -I../.. -I../.. -I../../src/client -I../../src/shared -I/usr/include/slang  -Wno-deprecated -I/usr/include/openssl -Wall  -g -O2 -MT common.o -MD -MP -MF .deps/common.Tpo -c -o common.o common.cpp
common.cpp:61: warning: deprecated conversion from string constant to &#8216;char*&#8217;
common.cpp: In function &#8216;void formatCompilOptions(char*, int)&#8217;:
common.cpp:82: warning: format not a string literal and no format arguments
common.cpp:82: warning: format not a string literal and no format arguments
mv -f .deps/common.Tpo .deps/common.Po
g++ -DHAVE_CONFIG_H -DLOCALEDIR=\"/usr/local/share/locale\" -D_REENTRANT -D_FILE_OFFSET_BITS=64 -I. -I../.. -I../.. -I../../src/client -I../../src/shared -I/usr/include/slang  -Wno-deprecated -I/usr/include/openssl -Wall  -g -O2 -MT access.o -MD -MP -MF .deps/access.Tpo -c -o access.o access.cpp
access.cpp: In function &#8216;unsigned int CheckAccess(bool, char*, char*)&#8217;:
access.cpp:141: warning: ignoring return value of &#8216;char* fgets(char*, int, FILE*)&#8217;, declared with attribute warn_unused_result
mv -f .deps/access.Tpo .deps/access.Po
g++ -DHAVE_CONFIG_H -DLOCALEDIR=\"/usr/local/share/locale\" -D_REENTRANT -D_FILE_OFFSET_BITS=64 -I. -I../.. -I../.. -I../../src/client -I../../src/shared -I/usr/include/slang  -Wno-deprecated -I/usr/include/openssl -Wall  -g -O2 -MT net.o -MD -MP -MF .deps/net.Tpo -c -o net.o net.cpp
In file included from net.cpp:22:
net.h:31:22: error: iostream.h: No such file or directory
make[3]: *** [net.o] Error 1
make[3]: Leaving directory `/home/aji/partimage-0.6.7/src/shared'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aji/partimage-0.6.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aji/partimage-0.6.7'
make: *** [all] Error 2
aji@aij-dtp:~/partimage-0.6.7$ 
```Please note, before telling me how *wrong* I am, I tried *make* without root privledges, got (make[2]: *** [all-recursive] Error 1) and Google told me to do it as root.
So far that hasn't proved. :)

partimage; [http://www.partimage.org/Download](http://www.partimage.org/Download)

Synaptic does *not* have Partimage, only its -doc for some reason..

---

### Post by halitech on 2009-07-01
why not install the version in the repo?

```
sudo apt-get install partimage
```

---

### Post by Elep.Repu on 2009-07-01
> **halitech said:**
> why not install the version in the repo?

```
sudo apt-get install partimage
```


I am AMD x86_64. There is not a version in the repository for my architecture.

---

### Post by halitech on 2009-07-01
from here: [http://www.partimage.org/Partimage-FAQ](http://www.partimage.org/Partimage-FAQ)

I have a non i386 architecture machine, will partimage/partimaged work on it?

> Quick answer: no. A bit longer, partimage/partimaged 0.6.x can't work on Big Endian machine. On Little Endian machine, you may have luck any make it working but you'll be on your own because we won't be able to help you. If someone has an old Sparc, HPUX, MIPS or whatever he doesn't use, please, give it to us and we'll be able to make partimage working on non-i386. 

I might be reading that wrong but I would think AMD64 is not i386 so partimage won't run or install.

---

