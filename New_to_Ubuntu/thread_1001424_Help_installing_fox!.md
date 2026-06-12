---
title: "Help installing fox!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by Excatog on 2008-12-03
Hey, new to the forums. Im using ubuntu I downloaded from a torrent site... It all seems to be working well. Im using it in an VMware VM. I am trying to install fox, so I can install FXRuby, so I can install ruby forger! Just doing some tinkering around with *nix systems and stuff to get used to bash and networking with bash. (going to school for network engineering and would like to get some hands on with *nix before my classes for it start)

Anywho, im trying to install fox and its not working :( I tried the ./configure and then make but its fubared. So I did some reading and tried it with the sudo command infront to do it as a root user would? Still didnt wory :( here is my terminal and the stuff it gives me... I really am not sure what im doing wrong, im sure its something obvious but I am completely oblivious to *nix stuff.... If this even is *nix stuff :O

I just want to get intimate with bash :)

Anywho, here is the terminal output.
```

checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
appending configuration tag "F77" to libtool
checking for X... no
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking host system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking whether byte ordering is bigendian... no
checking for QNX environment... no
checking for Sun WorkShop C++... no
checking for Xft support... 

checking for X11/extensions/shape.h... no

checking for X11/extensions/XShm.h... no
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking for thread-safe library calls... 
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_exit in -lpthread... yes
checking for sem_init in -lrt... yes

checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no

checking png.h usability... no
checking png.h presence... no
checking for png.h... no

checking tiff.h usability... no
checking tiff.h presence... no
checking for tiff.h... no

checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no

checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no

checking for X11/Xcursor/Xcursor.h... no

checking for X11/extensions/Xrandr.h... no

checking for vsscanf... yes
checking for vsnprintf... yes
checking for strtoll... yes
checking for strtoull... yes
checking for socket in -lsocket... no
checking for gethostbyaddr in -lnsl... yes
checking for dlopen in -ldl... yes
checking for shl_load in -ldld... no
checking for CUPS support... 
checking for debugging... 
checking for release build... 
checking for profiling... 
checking for OpenGL support... 
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/Makefile
config.status: WARNING:  include/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/fxver.h
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/version.rc
config.status: creating chart/Makefile
config.status: WARNING:  chart/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/art/Makefile
config.status: WARNING:  doc/art/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/screenshots/Makefile
config.status: WARNING:  doc/screenshots/Makefile.in seems to ignore the --datarootdir setting
config.status: creating tests/Makefile
config.status: WARNING:  tests/Makefile.in seems to ignore the --datarootdir setting
config.status: creating adie/Makefile
config.status: WARNING:  adie/Makefile.in seems to ignore the --datarootdir setting
config.status: creating shutterbug/Makefile
config.status: WARNING:  shutterbug/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pathfinder/Makefile
config.status: WARNING:  pathfinder/Makefile.in seems to ignore the --datarootdir setting
config.status: creating calculator/Makefile
config.status: WARNING:  calculator/Makefile.in seems to ignore the --datarootdir setting
config.status: creating windows/Makefile
config.status: WARNING:  windows/Makefile.in seems to ignore the --datarootdir setting
config.status: creating fox.spec
config.status: creating fox-config
config.status: creating fox.pc

Configure finished!
              Do:  'make' to compile FOX.
            Then:  'make install' to install it.

cr0vax@ub4r:~/Desktop/fox-1.6.34$ make
Making all in utils
make[1]: Entering directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fox\" -DVERSION=\"1.6.34\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_STRTOLL=1 -DHAVE_STRTOULL=1 -DHAVE_LIBDL=1 -I. -I.      -DFOX_THREAD_SAFE=1 -D_POSIX_PTHREAD_SEMANTICS -D_REENTRANT -D_GNU_SOURCE -DNO_XIM  -c reswrap.cpp
/bin/bash: g++: command not found
make[1]: *** [reswrap.o] Error 127
make[1]: Leaving directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
make: *** [all-recursive] Error 1
cr0vax@ub4r:~/Desktop/fox-1.6.34$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking major version... 1
checking minor version... 6
checking patchlevel... 34
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
appending configuration tag "F77" to libtool
checking for X... no
checking whether time.h and sys/time.h may both be included... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking host system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking whether byte ordering is bigendian... no
checking for QNX environment... no
checking for Sun WorkShop C++... no
checking for Xft support... 

checking for X11/extensions/shape.h... no

checking for X11/extensions/XShm.h... no
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking for thread-safe library calls... 
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_exit in -lpthread... yes
checking for sem_init in -lrt... yes

checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no

checking png.h usability... no
checking png.h presence... no
checking for png.h... no

checking tiff.h usability... no
checking tiff.h presence... no
checking for tiff.h... no

checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no

checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no

checking for X11/Xcursor/Xcursor.h... no

checking for X11/extensions/Xrandr.h... no

checking for vsscanf... yes
checking for vsnprintf... yes
checking for strtoll... yes
checking for strtoull... yes
checking for socket in -lsocket... no
checking for gethostbyaddr in -lnsl... yes
checking for dlopen in -ldl... yes
checking for shl_load in -ldld... no
checking for CUPS support... 
checking for debugging... 
checking for release build... 
checking for profiling... 
checking for OpenGL support... 
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/Makefile
config.status: WARNING:  include/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/fxver.h
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/version.rc
config.status: creating chart/Makefile
config.status: WARNING:  chart/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/art/Makefile
config.status: WARNING:  doc/art/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/screenshots/Makefile
config.status: WARNING:  doc/screenshots/Makefile.in seems to ignore the --datarootdir setting
config.status: creating tests/Makefile
config.status: WARNING:  tests/Makefile.in seems to ignore the --datarootdir setting
config.status: creating adie/Makefile
config.status: WARNING:  adie/Makefile.in seems to ignore the --datarootdir setting
config.status: creating shutterbug/Makefile
config.status: WARNING:  shutterbug/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pathfinder/Makefile
config.status: WARNING:  pathfinder/Makefile.in seems to ignore the --datarootdir setting
config.status: creating calculator/Makefile
config.status: WARNING:  calculator/Makefile.in seems to ignore the --datarootdir setting
config.status: creating windows/Makefile
config.status: WARNING:  windows/Makefile.in seems to ignore the --datarootdir setting
config.status: creating fox.spec
config.status: creating fox-config
config.status: creating fox.pc

Configure finished!
              Do:  'make' to compile FOX.
            Then:  'make install' to install it.

cr0vax@ub4r:~/Desktop/fox-1.6.34$ sudo make
Making all in utils
make[1]: Entering directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fox\" -DVERSION=\"1.6.34\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_STRTOLL=1 -DHAVE_STRTOULL=1 -DHAVE_LIBDL=1 -I. -I.      -DFOX_THREAD_SAFE=1 -D_POSIX_PTHREAD_SEMANTICS -D_REENTRANT -D_GNU_SOURCE -DNO_XIM  -c reswrap.cpp
/bin/bash: g++: command not found
make[1]: *** [reswrap.o] Error 127
make[1]: Leaving directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
make: *** [all-recursive] Error 1
cr0vax@ub4r:~/Desktop/fox-1.6.34$ 

```

---

### Post by binbash on 2008-12-03
/bin/bash: g++: command not found

try this : 

sudo apt-get install build-essential g++

---

### Post by Excatog on 2008-12-03
hey thanks a bunch! I entered the command and it did some stuff, looks like it downloaded something for the terminal to work with and it did some stuff and I dont really understand what it did exactly so an explanation would be cool if it isnt to much trouble! Anywho, it still doesnt work, but I very much appreciate that command, it got me further down the rabbit hole :D now I have.... 

```
cr0vax@ub4r:~/Desktop/fox-1.6.34$ make
Making all in utils
make[1]: Entering directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/cr0vax/Desktop/fox-1.6.34/utils'
Making all in include
make[1]: Entering directory `/home/cr0vax/Desktop/fox-1.6.34/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/cr0vax/Desktop/fox-1.6.34/include'
Making all in src
make[1]: Entering directory `/home/cr0vax/Desktop/fox-1.6.34/src'
/bin/bash ../libtool --mode=compile g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fox\" -DVERSION=\"1.6.34\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_STRTOLL=1 -DHAVE_STRTOULL=1 -DHAVE_LIBDL=1 -I. -I.  -I../include -I../include    -g -O2  -DFOX_THREAD_SAFE=1 -D_POSIX_PTHREAD_SEMANTICS -D_REENTRANT -D_GNU_SOURCE -DNO_XIM -Wall -W -Woverloaded-virtual -Wformat  -c FX88591Codec.cpp
 g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"fox\" -DVERSION=\"1.6.34\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_STRTOLL=1 -DHAVE_STRTOULL=1 -DHAVE_LIBDL=1 -I. -I. -I../include -I../include -g -O2 -DFOX_THREAD_SAFE=1 -D_POSIX_PTHREAD_SEMANTICS -D_REENTRANT -D_GNU_SOURCE -DNO_XIM -Wall -W -Woverloaded-virtual -Wformat -c FX88591Codec.cpp  -fPIC -DPIC -o .libs/FX88591Codec.o
In file included from FX88591Codec.cpp:1:
../include/xincs.h:188:19: error: X11/X.h: No such file or directory
../include/xincs.h:192:22: error: X11/Xlib.h: No such file or directory
../include/xincs.h:196:22: error: X11/Xcms.h: No such file or directory
../include/xincs.h:197:23: error: X11/Xutil.h: No such file or directory
../include/xincs.h:198:27: error: X11/Xresource.h: No such file or directory
../include/xincs.h:199:23: error: X11/Xatom.h: No such file or directory
../include/xincs.h:200:28: error: X11/cursorfont.h: No such file or directory
make[1]: *** [FX88591Codec.lo] Error 1
make[1]: Leaving directory `/home/cr0vax/Desktop/fox-1.6.34/src'
make: *** [all-recursive] Error 1
cr0vax@ub4r:~/Desktop/fox-1.6.34$ 

```

---

### Post by binbash on 2008-12-03
sudo apt-get install libx11-dev

---

### Post by Excatog on 2008-12-04
Awesome its all working it looks like! I typed in the make command and its doing all sorts of crazy stuff I dont understand. Wee. Ill let you know how it goes and if it works, hopefully the rest of the installation will go off without a hitch :D

Thanks for the commands binbash. Much appreciated.

Lets hope the make install works now to >.<

---

### Post by Excatog on 2008-12-04
Sorry for double posting, but id rather condense my issue into one thread.

As far as I can tell fox installed correctly but...

My FXRuby just doesnt feel like installing one bit, I really feel like a leech of a noob for asking all these questions but I have absolutely NO IDEA to as what im read doing. Navigating via bash is fine, executing unpack, compile and install commands is a different story though. A whole new book to read aye?

Anywho, this is what im getting when I try to install FXRuby...

```
cr0vax@ub4r:~$ cd Desktop
cr0vax@ub4r:~/Desktop$ cd FXR*
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$ dir
doap.rdf  FXRuby-ruby1.8.6-i386-msvcrt.iss  pre-config.rb  README.win32.txt
doc	  install.rb			    Rakefile	   scripts
examples  lib				    rdoc-sources   swig-interfaces
ext	  LICENSE			    README	   tests
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$ ruby install.rb config
install.rb: entering config phase...
---> lib
---> lib/fox16
<--- lib/fox16
<--- lib
---> ext
---> ext/fox16
/usr/bin/ruby1.8 /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb 
/home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb:8:in `require': no such file to load -- mkmf (LoadError)
	from /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb:8
config failed
'system /usr/bin/ruby1.8 /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb ' failed
Try 'ruby install.rb --help' for detailed usage.
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$ 

```

After successfully installing fox... I think. When I did the make install command on the fox make files it all seemed to go through and finished up with no error messages, now there is a no folder called windows in there with some wierd folder names and makefiles. Not sure if im supposed to take that a step further or not or what...

So really all I can gather with my extremely limited ubuntu knowledge from the output in terminal is that I am missing a require file or something? Not sure what to make of it...

Thx for any help guys!

Let me know where I screwed up :(

---

### Post by loell on 2008-12-04
actually **fox 1.6 **is in the repository,

you can install it by

```
sudo apt-get install libfox-1.6-0 libfox-1.6-dev
```

---

### Post by Excatog on 2008-12-08
Hey thanks for that command! I read up on respositorys because I wasnt sure to as what it was and its pretty interesting stuff. Is there a directory of these repositorys? They might make my life alot easier....

heh...

thx!

Also, the FXRuby still doesnt want to install, should I make a new thread for all this or keep it here? I installed fox, I think... Anyways, here is what im getting and the repository thing did stuff but it still wont install...

```
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$ ruby install.rb config
install.rb: entering config phase...
---> lib
---> lib/fox16
<--- lib/fox16
<--- lib
---> ext
---> ext/fox16
/usr/bin/ruby1.8 /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb 
/home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb:8:in `require': no such file to load -- mkmf (LoadError)
	from /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb:8
config failed
'system /usr/bin/ruby1.8 /home/cr0vax/Desktop/FXRuby-1.6.16/ext/fox16/extconf.rb ' failed
Try 'ruby install.rb --help' for detailed usage.
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$
```

As far as I can tell its missing a require file or something? or mkmf file? Im not sure what to make of the output...

I iz a nub :(

---

### Post by loell on 2008-12-08
can you post what version of ruby  you're using?


```
ruby --version
```

---

### Post by Excatog on 2008-12-08
```
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$ ruby --version
ruby 1.8.7 (2008-08-11 patchlevel 72) [i486-linux]
cr0vax@ub4r:~/Desktop/FXRuby-1.6.16$
```

---

