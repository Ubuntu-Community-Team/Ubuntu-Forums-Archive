---
title: "To include graphics.h and conio.h headers files in gcc++ compiler"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-31
HI!
I am using gcc++ compiler to run c/c++ under linux-ubuntu.
But I am gettin problem in in compilin the programs.
I want to include all the files and headers of turbo c in gcc++ compiler.
I am a student and in this semester i have this subject called COMPUTER GRAPHICS. In this we need to draw lines and circles and etc...using graphics.h headers files that i can't found in gcc++ compilers.

I have downloaded this libgraph.tar.gz package but couldn't install it.
Help me please.
thanks!

---

### Post by krishnandu.sarkar on 2010-07-31
I'm not sure about graphics.h but conio.h is not there, and you won't need that too. Try compiling programs excluding conio.h. And for graphics.h please wait for someone who knows about it.

---

### Post by amityadav9314 on 2010-07-31
WHat...no one here can help me....


here is link in which some idea is given, i tried that but i am gettin some sort of error...


[http://my.opera.com/nikbhardwaj/blog/show.dml/9406191](http://my.opera.com/nikbhardwaj/blog/show.dml/9406191)



Now i hope i can be helped....

---

### Post by gsocker on 2010-07-31
Both are DOS/Windows specific headers and do not exist on Linux.

conio.h is the old DOS console io functions. 
graphics.h is a Borland/and possibly Microsoft C graphics library, also from the days of yore. 

If you need something similar to conio you will need to look into either ncurses or slang.

As for the graphics.h replacement, please post the error messages you are  getting.

---

### Post by amityadav9314 on 2010-07-31
the followin is the error that i am gettin



```
amit@ubuntu:~$ cd libgraph-1.0.2
amit@ubuntu:~/libgraph-1.0.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for gawk... (cached) gawk
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
amit@ubuntu:~/libgraph-1.0.2$
```

---

### Post by Paul820 on 2010-07-31
> configure: error: *** SDL version 1.2.0 not found!

Maybe you need SDL version >= 1.2.0

EDIT: You should read all the errors, linux is fantastic at telling you what you need to know if you would only read the help it gives you!

---

### Post by amityadav9314 on 2010-07-31
but what is sdl version and how and what i need to do...
i am a newbie, so can't get it, sorry.

---

### Post by Paul820 on 2010-07-31
Just go to synaptic package manager, search for '**sdl**', get the version 1.2.0 or above and install it, you will need the package that ends in **dev** for the development header files.

---

