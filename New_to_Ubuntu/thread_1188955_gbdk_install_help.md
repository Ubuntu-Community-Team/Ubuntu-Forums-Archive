---
title: "gbdk install help"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by divindavid on 2009-06-16
Hello, I've been running ubuntu and other flavors of linux for a good 3 or 4 years now. But when it comes to installing programs I would just look in the repos or find a .deb. I'm looking to install gbdk (GameBoy Dev. Kit) it is a C compiler for the Gameboy and Gameboy Color. I downloaded it and there is only a folder with collection of other folders and .make files (they are actually ending in .mak sometimes)

file:///home/david/Desktop/gbdk/README

file:///home/david/Desktop/gbdk/mega.mak

file:///home/david/Desktop/gbdk/Makefile

file:///home/david/Desktop/gbdk/ChangeLog

file:///home/david/Desktop/gbdk/build.mak

file:///home/david/Desktop/gbdk/sdcc

file:///home/david/Desktop/gbdk/libc

file:///home/david/Desktop/gbdk/lib

file:///home/david/Desktop/gbdk/include

file:///home/david/Desktop/gbdk/gbdk-support

file:///home/david/Desktop/gbdk/gbdk-lib

file:///home/david/Desktop/gbdk/examples

file:///home/david/Desktop/gbdk/doc

file:///home/david/Desktop/gbdk/bin


Those are the list of files within the gbdk folder. I know I have to run some sort of make command in the terminal. I have tried to google this, but no luck. If someone could point me into the correct direction or show what I should do that would be great.

I'm running xubuntu 9.04

Thank you.

---

### Post by Mornedhel on 2009-06-16
Have you read the README file ?... Those usually contain instructions on how to build and install from source. If you have and you're still confused, make sure you have gcc and make installed, and try

```
make
```
```
sudo make install
```

I notice there is a /bin folder, have you tried cd'ing into that and are there any precompiled binaries inside ?

---

### Post by divindavid on 2009-06-16
Thank you. I cd'ed into the gbdk folder and did the sudo make install but here is the output 


```
david@david-laptop:~$ cd /home/david/Desktop/gbdk
david@david-laptop:~/Desktop/gbdk$ sudo make install
cd /home/david/Desktop/gbdk/sdcc; CC=gcc CXX=g++ STRIP=strip RANLIB=ranlib CXXFLAGS= ./configure --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2
creating cache ./config.cache
checking for mawk... mawk
checking version of the package... 2.3.1
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... g++
checking whether the C++ compiler (g++  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.
make: *** [/home/david/Desktop/gbdk/sdcc/sdccconf.h] Error 1
david@david-laptop:~/Desktop/gbdk$ 

```
I'm not to sure what to do. I'll cd into the bin folder. Do you think I should change the extentions from .mak to .make?

---

### Post by Cheesemill on 2009-06-16
The first step is to make sure you have all the required tools installed.
Do a
```
apt-get update && apt-get install build-essential
```
and see if this helps.

---

### Post by Mornedhel on 2009-06-16
No, don't try changing the filenames. It will most likely not work and break something else.

What I meant was for you to run both commands in succession : first make then sudo make install. There is a Makefile there, so it *should* work. Hopefully.

This should not be the first thing you do, however. First thing should have been checking what's in the /bin directory in case the application is precompiled ; then you should have checked the contents of the README file, since it most likely explains how to install the application. Only then, once you have exhausted any possible source of information (including the application's homepage and/or online FAQ), should you be doing what we are doing now, which is trying things at half-random until something works.

---

### Post by divindavid on 2009-06-16
> **Cheesemill said:**
> The first step is to make sure you have all the required tools installed.
Do a
```
apt-get update && apt-get install build-essential
```
and see if this helps.

I can that, and it did its thing downloading what it needed. And than I tried to run the sudo make install. I got this 

```
root@david-laptop:/home/david# cd /home/david/Desktop/gbdk
root@david-laptop:/home/david/Desktop/gbdk# sudo make install
cd /home/david/Desktop/gbdk/sdcc; CC=gcc CXX=g++ STRIP=strip RANLIB=ranlib CXXFLAGS= ./configure --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2
loading cache ./config.cache
checking for mawk... mawk
checking version of the package... 2.3.1
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... g++
checking whether the C++ compiler (g++  ) works... yes
checking whether the C++ compiler (g++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for flex... lex
checking for yywrap in -ll... no
checking for bison... :
checking for autoconf... :
checking for strip... strip
checking for as... as
checking for cp... cp
configure: error: Cannot find required program bison.
make: *** [/home/david/Desktop/gbdk/sdcc/sdccconf.h] Error 1
root@david-laptop:/home/david/Desktop/gbdk# 

```

I think I need a program called bison. I don't know.

---

### Post by Mornedhel on 2009-06-16
Try installing bison (sudo apt-get install bison) and run make again.

I feel like I'm repeating myself, but have you read the README file ?

---

### Post by divindavid on 2009-06-16
Yes, I installed bison and tried the sudo make install again. 
Here are the results 

```
root@david-laptop:~# cd /home/david/Desktop/gbdk
root@david-laptop:/home/david/Desktop/gbdk# sudo make install
cd /home/david/Desktop/gbdk/sdcc; CC=gcc CXX=g++ STRIP=strip RANLIB=ranlib CXXFLAGS= ./configure --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2
loading cache ./config.cache
checking for mawk... mawk
checking version of the package... 2.3.1
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... g++
checking whether the C++ compiler (g++  ) works... yes
checking whether the C++ compiler (g++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for flex... flex
checking for yywrap in -lfl... yes
checking for bison... bison -y
checking for autoconf... :
checking for strip... strip
checking for as... as
checking for cp... cp
checking for ANSI C header files... yes
checking for getopt.h... yes
checking for unistd.h... yes
checking for endian.h... yes
checking for machine/endian.h... no
checking for malloc.h... yes
checking for sys/isa_defs.h... no
checking for sys/socket.h... yes
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking which header file defines FD_ macros... 
checking for strlen... yes
checking for strcpy... yes
checking for strcat... yes
checking for strstr... yes
checking for strcmp... yes
checking for strerror... yes
checking for strtok... yes
checking for strdup... yes
checking for strchr... yes
checking for memcpy... yes
checking for fgets... yes
checking for yylex... no
checking for library containing socket... none required
checking for library containing inet_addr... none required
checking whether preprocessor accepts -MM or -M... -MM
checking whether gcc accepts -ggdb... yes
checking whether gcc accepts -pipe... yes
checking return type of signal handlers... void
updating cache ./config.cache
creating ./config.status
creating main.mk
creating src/Makefile
creating as/mcs51/Makefile
creating device/include/Makefile
creating device/lib/Makefile
creating debugger/mcs51/Makefile
creating Makefile.common
creating sdccconf.h
configuring in support/cpp2
running /bin/sh ./configure  --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2 --cache-file=../.././config.cache --srcdir=.
loading cache ../.././config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... (cached) gcc -E
checking for inline... inline
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking execution character set... ASCII
checking whether make sets ${MAKE}... yes
checking whether a default assembler was specified... no
checking whether a default linker was specified... no
checking for GNU C library... yes
checking whether ln works... yes
checking whether ln -s works... yes
checking for ranlib... (cached) ranlib
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether string.h and strings.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for limits.h... yes
checking for stddef.h... yes
checking for string.h... yes
checking for strings.h... yes
checking for stdlib.h... yes
checking for time.h... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking for sys/file.h... yes
checking for sys/time.h... yes
checking for sys/resource.h... yes
checking for sys/param.h... yes
checking for sys/times.h... yes
checking for sys/stat.h... yes
checking for direct.h... no
checking for malloc.h... (cached) yes
checking for langinfo.h... yes
checking for CHAR_BIT... yes
checking byte ordering... little-endian
checking for mktemp... yes
checking for strip... (cached) strip
checking for preprocessor stringizing operator... yes
checking for inttypes.h... yes
checking for times... yes
checking for clock... yes
checking for strchr... (cached) yes
checking for strrchr... yes
checking for lstat... yes
checking for ssize_t... yes
checking for getpagesize... yes
checking for working mmap from /dev/zero... yes
checking for working mmap with MAP_ANON(YMOUS)... yes
checking for working mmap of a file... yes
checking whether getenv is declared... no
checking whether abort is declared... no
checking whether errno is declared... no
checking whether malloc is declared... no
checking whether realloc is declared... no
checking whether calloc is declared... no
checking whether free is declared... no
checking whether getopt is declared... no
checking whether clock is declared... no
checking whether times is declared... no
checking for struct tms... no
checking for clock_t... no
checking if mkdir takes one argument... no
creating cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for inline... inline
checking size of short... 2
checking size of int... 4
checking size of long... 4
checking execution character set... ASCII
checking whether make sets ${MAKE}... yes
checking whether a default assembler was specified... no
checking whether a default linker was specified... no
checking for GNU C library... yes
checking whether ln works... yes
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether string.h and strings.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for limits.h... yes
checking for stddef.h... yes
checking for string.h... yes
checking for strings.h... yes
checking for stdlib.h... yes
checking for time.h... yes
checking for fcntl.h... yes
checking for unistd.h... yes
checking for sys/file.h... yes
checking for sys/time.h... yes
checking for sys/resource.h... yes
checking for sys/param.h... yes
checking for sys/times.h... yes
checking for sys/stat.h... yes
checking for direct.h... no
checking for malloc.h... yes
checking for langinfo.h... yes
checking for CHAR_BIT... yes
checking byte ordering... little-endian
checking for mktemp... yes
checking for strip... strip
checking for preprocessor stringizing operator... yes
checking for inttypes.h... yes
checking for times... yes
checking for clock... yes
checking for strchr... yes
checking for strrchr... yes
checking for lstat... yes
checking for ssize_t... yes
checking for getpagesize... yes
checking for working mmap from /dev/zero... yes
checking for working mmap with MAP_ANON(YMOUS)... yes
checking for working mmap of a file... yes
checking whether getenv is declared... no
checking whether abort is declared... no
checking whether errno is declared... no
checking whether malloc is declared... no
checking whether realloc is declared... no
checking whether calloc is declared... no
checking whether free is declared... no
checking whether getopt is declared... no
checking whether clock is declared... no
checking whether times is declared... no
checking for struct tms... no
checking for clock_t... no
checking if mkdir takes one argument... no
checking what assembler to use... /usr/bin/as
checking what nm to use... nm
checking whether to enable maintainer-specific portions of Makefiles... no
updating cache ./config.cache
creating ./config.status
creating Makefile
creating auto-host.h
checking what assembler to use... 
checking what nm to use... 
checking whether to enable maintainer-specific portions of Makefiles... no
updating cache ../.././config.cache
creating ./config.status
creating Makefile
creating auto-host.h
configuring in packihx
running /bin/sh ./configure  --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2 --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking size of char... 1
checking size of short... (cached) 2
checking size of int... (cached) 4
checking size of long... (cached) 4
checking size of long long... 8
checking type name for byte... char
checking type name for word... short
updating cache .././config.cache
creating ./config.status
creating Makefile
creating config.h
config.h is unchanged
configuring in sim/ucsim
running /bin/sh ./configure  --disable-mcs51-port --disable-avr-port --disable-ds390-port --disable-pic-port --disable-i186-port --disable-tlcs900h-port --disable-ucsim --disable-device-lib-build --disable-packihx --prefix=/opt/gbdk --program-suffix= --host=ppc-unknown-linux2.2 --cache-file=../.././config.cache --srcdir=.
loading cache ../.././config.cache
checking for mawk... (cached) mawk
checking version of the package... 0.3.2-pre1
checking for c++... (cached) g++
checking whether the C++ compiler (g++  ) works... yes
checking whether the C++ compiler (g++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for ANSI C header files... (cached) yes
checking for getopt.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/socket.h... (cached) yes
checking for dlfcn.h... yes
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking which header file defines FD_ macros... <sys/types.h>
checking for socket in -lsocket... no
checking for xdr_short in -lnsl... yes
checking for dlopen in -ldl... yes
checking for panel_above in -lpanel... no
checking for nl in -lcurses... no
checking for vprintf... yes
checking for vsnprintf... yes
checking for vasprintf... yes
checking for strlen... (cached) yes
checking for strcpy... (cached) yes
checking for strcat... (cached) yes
checking for strstr... (cached) yes
checking for strcmp... (cached) yes
checking for strerror... (cached) yes
checking for strtok... (cached) yes
checking for strdup... (cached) yes
checking for strchr... (cached) yes
checking for memcpy... (cached) yes
checking for fgets... (cached) yes
checking for yylex... (cached) no
checking whether scanf knows %a... no
checking whether getcwd is GNUish... no
checking for type of length pointer parameter of accept... size_t
checking whether byte ordering is bigendian... no
checking whether preprocessor accepts -MM or -M... -MM
checking whether g++ accepts -ggdb... no
checking whether g++ accepts -pipe... no
checking whether g++ accepts -fPIC... no
checking whether g++ accepts -fpic... no
checking return type of signal handlers... (cached) void
checking size of char... (cached) 1
checking size of short... (cached) 2
checking size of int... (cached) 4
checking size of long... (cached) 4
checking size of long long... (cached) 8
checking type name for byte... char
checking type name for word... short
checking type name for dword... int
updating cache ../.././config.cache
creating ./config.status
creating main.mk
creating sim.src/Makefile
creating cmd.src/Makefile
creating s51.src/Makefile
creating avr.src/Makefile
creating z80.src/Makefile
creating gui.src/Makefile
creating gui.src/serio.src/Makefile
creating doc/Makefile
creating ddconfig.h
make -C /home/david/Desktop/gbdk/sdcc SDCC_SUB_VERSION=gbdk-2.96a
make[1]: Entering directory `/home/david/Desktop/gbdk/sdcc'
for lib in support/cpp2 support/makebin; do make -C $lib; done
make[2]: Entering directory `/home/david/Desktop/gbdk/sdcc/support/cpp2'
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cppmain.c -o cppmain.o
gcc       -DHAVE_CONFIG_H    -I. -I./libiberty \
	  -DLOCALEDIR=\"\" \
	  -c ./intl.c
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty libiberty/safe-ctype.c -o safe-ctype.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty libiberty/obstack.c -o obstack.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty libiberty/splay-tree.c -o splay-tree.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty libiberty/lbasename.c -o lbasename.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cpplib.c -o cpplib.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cpplex.c -o cpplex.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cppmacro.c -o cppmacro.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cppexp.c -o cppexp.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cppfiles.c -o cppfiles.o
cppfiles.c: In function ‘read_include_file’:
cppfiles.c:386: warning: format ‘%lu’ expects type ‘long unsigned int’, but argument 5 has type ‘int’
cppfiles.c:425: warning: format ‘%u’ expects type ‘unsigned int’, but argument 4 has type ‘__off_t’
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cpphash.c -o cpphash.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cpperror.c -o cpperror.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty cppinit.c -o cppinit.o
gcc       -DHAVE_CONFIG_H    -I. -I./libiberty \
	  -DGCC_INCLUDE_DIR=\"/include\" -DGPLUSPLUS_INCLUDE_DIR=\"\" -DGPLUSPLUS_TOOL_INCLUDE_DIR=\"/\" -DGPLUSPLUS_BACKWARD_INCLUDE_DIR=\"/backward\" -DLOCAL_INCLUDE_DIR=\"/usr/local/include\" -DCROSS_INCLUDE_DIR=\"/sys-include\" -DTOOL_INCLUDE_DIR=\"/include\" \
	  -c ./cppdefault.c
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty hashtable.c -o hashtable.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty mkdeps.c -o mkdeps.o
gcc       -DHAVE_CONFIG_H    -I. -I./libiberty \
	-DPREFIX=\"/opt/gbdk\" \
	  -c ./prefix.c
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty version.c -o version.o
gcc -c       -DHAVE_CONFIG_H    -I. -I./libiberty mbchar.c -o mbchar.o
rm -rf libcpp.a
ar rc libcpp.a cpplib.o cpplex.o cppmacro.o cppexp.o cppfiles.o cpphash.o cpperror.o cppinit.o cppdefault.o hashtable.o mkdeps.o prefix.o version.o mbchar.o
ranlib libcpp.a
gcc       -DHAVE_CONFIG_H  -o ../../bin/sdcpp cppmain.o \
	safe-ctype.o obstack.o splay-tree.o lbasename.o libcpp.a 
make[2]: Leaving directory `/home/david/Desktop/gbdk/sdcc/support/cpp2'
make[2]: Entering directory `/home/david/Desktop/gbdk/sdcc/support/makebin'
gcc -ggdb -O2 -pipe -Wall  -I. -I../.. -I../../support/Util  -c -o makebin.o makebin.c
makebin.c: In function ‘main’:
makebin.c:75: warning: implicit declaration of function ‘memset’
makebin.c:75: warning: incompatible implicit declaration of built-in function ‘memset’
gcc -o ../../bin/makebin makebin.o
make[2]: Leaving directory `/home/david/Desktop/gbdk/sdcc/support/makebin'
make -C src
make[2]: Entering directory `/home/david/Desktop/gbdk/sdcc/src'
Makefile:90: Makefile.dep: No such file or directory
gcc -E  -I. -I.. -I../support/Util -MM SDCCy.c SDCChasht.c SDCCmain.c SDCCsymt.c SDCCopt.c SDCCast.c SDCCmem.c SDCCval.c SDCCicode.c SDCCbitv.c SDCCset.c SDCClabel.c SDCCBBlock.c SDCCloop.c SDCCcse.c SDCCcflow.c SDCCdflow.c SDCClrange.c SDCCptropt.c SDCCpeeph.c SDCCglue.c spawn.c asm.c SDCCmacro.c SDCCutil.c SDCClex.c >Makefile.dep
make[2]: Leaving directory `/home/david/Desktop/gbdk/sdcc/src'
make[2]: Entering directory `/home/david/Desktop/gbdk/sdcc/src'
for i in z80; do make -C $i; done
make[3]: Entering directory `/home/david/Desktop/gbdk/sdcc/src/z80'
../port.mk:44: Makefile.dep: No such file or directory
mawk -f ../SDCCpeeph.awk peeph.def > peeph.rul
mawk -f ../SDCCpeeph.awk peeph-gbz80.def > peeph-gbz80.rul
mawk -f ../SDCCpeeph.awk peeph-z80.def > peeph-z80.rul
gcc -E -I.. -I. -I../.. -I../../support/Util -MM gen.c main.c ralloc.c support.c >Makefile.dep
make[3]: Leaving directory `/home/david/Desktop/gbdk/sdcc/src/z80'
make[3]: Entering directory `/home/david/Desktop/gbdk/sdcc/src/z80'
gcc -ggdb -O2 -pipe -Wall -I.. -I. -I../.. -I../../support/Util  -c -o gen.o gen.c
gcc -ggdb -O2 -pipe -Wall -I.. -I. -I../.. -I../../support/Util  -c -o main.o main.c
gcc -ggdb -O2 -pipe -Wall -I.. -I. -I../.. -I../../support/Util  -c -o ralloc.o ralloc.c
gcc -ggdb -O2 -pipe -Wall -I.. -I. -I../.. -I../../support/Util  -c -o support.o support.c
rm -f port.a
ar r port.a gen.o main.o ralloc.o support.o
ar: creating port.a
ranlib port.a
make[3]: Leaving directory `/home/david/Desktop/gbdk/sdcc/src/z80'
gcc -ggdb -O2 -pipe -Wall -DSDCC_SUB_VERSION_STR=\"gbdk-2.96a\"  -I. -I.. -I../support/Util -c ../support/Util/SDCCerr.c -o SDCCerr.o
gcc -ggdb -O2 -pipe -Wall -DSDCC_SUB_VERSION_STR=\"gbdk-2.96a\"  -I. -I.. -I../support/Util -c ../support/Util/NewAlloc.c -o NewAlloc.o
gcc -ggdb -O2 -pipe -Wall -DSDCC_SUB_VERSION_STR=\"gbdk-2.96a\"  -I. -I.. -I../support/Util -c ../support/Util/MySystem.c -o MySystem.o
gcc -ggdb -O2 -pipe -Wall -DSDCC_SUB_VERSION_STR=\"gbdk-2.96a\"  -I. -I.. -I../support/Util -c ../support/Util/BuildCmd.c -o BuildCmd.o
gcc -ggdb -O2 -pipe -Wall -DSDCC_SUB_VERSION_STR=\"gbdk-2.96a\"  -I. -I.. -I../support/Util -c SDCCy.c -o SDCCy.o
SDCC.y: In function ‘yyparse’:
SDCC.y:1004: error: label at end of compound statement
make[2]: *** [SDCCy.o] Error 1
make[2]: Leaving directory `/home/david/Desktop/gbdk/sdcc/src'
make[1]: *** [sdcc-cc] Error 2
make[1]: Leaving directory `/home/david/Desktop/gbdk/sdcc'
make: *** [sdcc-build] Error 2
root@david-laptop:/home/david/Desktop/gbdk# 

```


I have read the read me file. The install instructions for linux arnt amazing if anything they are very very brief

This is a the section from the readme about a linux install.

> Linux:

* Very similar to win32

* Extract the archive somewhere (normally /usr/lib/gbdk)

* Set GBDKDIR to where you installed with a trailing /

* Try compiling the examples as above 

It says I don't have permission to extract files to the /usr/lib/ folder.

Thank you all very much for you're help so far.

---

### Post by davisr on 2009-06-25
The GBDK does not compile completely with modern GCC versions; if you look in your Makefile output, you'll see that SDCC was never compiled.  The precompiled binaries for Linux systems are already posted on SourceForge [here]("http://sourceforge.net/project/downloading.php?group_id=1249&filename=gbdk-2.96a-i586-pc-linux2.2.tar.gz&a=6045950").  Just copy the gbdk folder to /opt/gbdk and link /opt/gbdk/bin/lcc to /usr/bin/lcc.  Then, you should be able to use the lcc command anywhere.

---

