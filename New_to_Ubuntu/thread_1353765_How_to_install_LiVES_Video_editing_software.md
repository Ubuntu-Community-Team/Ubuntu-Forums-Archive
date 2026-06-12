---
title: "How to install LiVES Video editing software"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by djftl on 2009-12-13
Hi there,

I just downloaded LiVES 1.0.6 to my desktop and I can't install it.
When I type: sudo: home/djftl/Desktop/lives-1.0.6/makefile: command not found:
it says command not found.
This is what it says on the install text. Since i'm new on Linux Ubuntu  I can't get to install this software. Please help.

"The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.

     Running `configure' might take a while.  While running, it prints
     some messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

  6. Often, you can also type `make uninstall' to remove the installed
     files again."

Thanks

Tobela

---

### Post by lisati on 2009-12-13
You need to extract the archive to its own directory first. Then do a "cd" to that directory, and the commands in the guide should work.

---

### Post by djftl on 2009-12-13
Thanks i've done that but now I received an error after typed make see below:

"djftl@ubuntu:~/Desktop/lives-1.0.6$ make
Making all in libOSC
make[1]: Entering directory `/home/djftl/Desktop/lives-1.0.6/libOSC'
Making all in .
make[2]: Entering directory `/home/djftl/Desktop/lives-1.0.6/libOSC'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/libOSC'
Making all in client
make[2]: Entering directory `/home/djftl/Desktop/lives-1.0.6/libOSC/client'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/libOSC/client'
Making all in sendOSC
make[2]: Entering directory `/home/djftl/Desktop/lives-1.0.6/libOSC/sendOSC'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/libOSC/sendOSC'
make[1]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/libOSC'
Making all in intl
make[1]: Entering directory `/home/djftl/Desktop/lives-1.0.6/intl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/intl'
Making all in libweed
make[1]: Entering directory `/home/djftl/Desktop/lives-1.0.6/libweed'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/libweed'
Making all in src
make[1]: Entering directory `/home/djftl/Desktop/lives-1.0.6/src'
gcc -DPACKAGE_NAME=\"LiVES\" -DPACKAGE_TARNAME=\"lives\" -DPACKAGE_VERSION=\"1.0.6\" -DPACKAGE_STRING=\"LiVES\ 1.0.6\" -DPACKAGE_BUGREPORT=\"http://www.sourceforge.net/tracker/\?group_id=64341\&atid=507139\" -DPACKAGE_URL=\"\" -DPACKAGE=\"lives\" -DVERSION=\"1.0.6\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -D__EXTENSIONS__=1 -D_ALL_SOURCE=1 -D_GNU_SOURCE=1 -D_POSIX_PTHREAD_SEMANTICS=1 -D_TANDEM_SOURCE=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DSTDC_HEADERS=1 -D_FILE_OFFSET_BITS=64 -DGETTEXT_PACKAGE=\"lives\" -DLOCALEDIR=\"\$\{datarootdir\}/locale\" -DPREFIX=\"NONE\" -DLiVES_VERSION=\"1.0.6\" -DHAVE_ALLOCA_H=1 -DHAVE_ALLOCA=1 -DHAVE_STDLIB_H=1 -DHAVE_UNISTD_H=1 -DHAVE_GETPAGESIZE=1 -DHAVE_MMAP=1 -DINTDIV0_RAISES_SIGFPE=1 -DHAVE_INTTYPES_H_WITH_UINTMAX=1 -DHAVE_STDINT_H_WITH_UINTMAX=1 -DHAVE_UNSIGNED_LONG_LONG=1 -DHAVE_UINTMAX_T=1 -DHAVE_INTTYPES_H=1 -DHAVE_ARGZ_H=1 -DHAVE_LIMITS_H=1 -DHAVE_LOCALE_H=1 -DHAVE_NL_TYPES_H=1 -DHAVE_MALLOC_H=1 -DHAVE_STDDEF_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_FEOF_UNLOCKED=1 -DHAVE_FGETS_UNLOCKED=1 -DHAVE_GETC_UNLOCKED=1 -DHAVE_GETCWD=1 -DHAVE_GETEGID=1 -DHAVE_GETEUID=1 -DHAVE_GETGID=1 -DHAVE_GETUID=1 -DHAVE_MEMPCPY=1 -DHAVE_MUNMAP=1 -DHAVE_PUTENV=1 -DHAVE_SETENV=1 -DHAVE_SETLOCALE=1 -DHAVE_STPCPY=1 -DHAVE_STRCASECMP=1 -DHAVE_STRDUP=1 -DHAVE_STRTOUL=1 -DHAVE_TSEARCH=1 -DHAVE___ARGZ_COUNT=1 -DHAVE___ARGZ_STRINGIFY=1 -DHAVE___ARGZ_NEXT=1 -DHAVE___FSETLOCKING=1 -DHAVE_ICONV=1 -DICONV_CONST= -DHAVE_LANGINFO_CODESET=1 -DHAVE_LC_MESSAGES=1 -DENABLE_NLS=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DHAVE_LIBDL=1 -DHAVE_POSIX_MEMALIGN=1 -DHAVE_LINUX_JOYSTICK_H=1 -I. -DPACKAGE_DATA_DIR=\""/usr/share"\" -DLIVES_DIR=\"""\" -DPACKAGE_LOCALE_DIR=\""/usr/share/locale"\" -I .. -I ../libOSC -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -O3       -DIS_LINUX_GNU=1 -DENABLE_OSC=1 -DLIVES_LIBDIR=\""/usr/lib"\" -g -O2 -Wall -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c:1060: error: expected identifier or ‘(’ before ‘}’ token
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/djftl/Desktop/lives-1.0.6/src'
make: *** [all-recursive] Error 1
djftl@ubuntu:~/Desktop/lives-1.0.6$ "
How can I correct this error?

---

### Post by pakki on 2010-04-11
usama@usama-desktop:~$ cd lives-1.3.2
bash: cd: lives-1.3.2: No such file or directory
usama@usama-desktop:~$ cd Desktop
usama@usama-desktop:~/Desktop$ cd lives-1.3.2
usama@usama-desktop:~/Desktop/lives-1.3.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for ANSI C header files... (cached) yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking dependency style of gcc... gcc3
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for lives-plugins/Makefile.am... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... (cached) ranlib
checking for simple visibility declarations... yes
checking for size_t... yes
checking for stdint.h... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for unsigned long long int... yes
checking for inttypes.h... (cached) yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether imported symbols can be declared weak... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_kill in -lpthread... yes
checking for pthread_rwlock_t... yes
checking for multithread API to use... posix
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking for inttypes.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for argz_count... yes
checking for argz_stringify... yes
checking for argz_next... yes
checking for __fsetlocking... yes
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for NL_LOCALE_NAME macro... yes
checking for bison... no
checking for long long int... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ptrdiff_t... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for asprintf... yes
checking for fwprintf... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for wcslen... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether getc_unlocked is declared... yes
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for open in -ldl... yes
checking for posix_memalign... yes
checking for perl... /usr/bin/perl
checking for pkg-config... /usr/bin/pkg-config
checking linux/joystick.h usability... yes
checking linux/joystick.h presence... yes
checking for linux/joystick.h... yes
checking for jack_get_client_name in -ljack... no
checking pkg-config is at least version 0.9.0... yes
checking for X11... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.4.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

usama@usama-desktop:~/Desktop/lives-1.3.2$ apt-get install gtk+-2.0
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
usama@usama-desktop:~/Desktop/lives-1.3.2$ sudo apt-get install gtk+-2.0
[sudo] password for usama: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk+-2.0
usama@usama-desktop:~/Desktop/lives-1.3.2$ 


**[COLOR="Blue"]cannot install it either ther is no package like gtk+-2.0[/COLOR]**

---

### Post by WinterRain on 2010-04-11
*Or* to get the latest Lives, just do:
```
sudo add-apt-repository ppa:hrickards/lives
sudo apt-get update && sudo apt-get install lives
```

---

### Post by no2498 on 2010-04-11
you can get lives in a deb file

hope this helps

---

### Post by salsaman on 2010-04-12
To build from source you will need libgtk2.0-dev.

---

