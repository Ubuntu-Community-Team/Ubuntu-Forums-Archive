---
title: "error when installed &quot;no package gtkmm-2.0 found&quot;"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by simtaalo on 2008-12-18
i'm trying to install gaiptek. i run ./autogen.sh in the directory and get this output

```
 ~/unified_package/src/gaiptek $ ./autogen.sh
Found GNU Make at /usr/bin/make ... good.
This script runs configure and make...
You did remember necessary arguments for configure, right?
./autogen.sh: 28: libtoolize: not found
gettextize: *** po/Makefile.in.in exists: use option -f if you really want to delete it.
gettextize: *** Stop.
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:389: AC_USE_SYSTEM_EXTENSIONS is expanded from...
aclocal.m4:2256: gl_LOCK_EARLY_BODY is expanded from...
aclocal.m4:2249: gl_LOCK_EARLY is expanded from...
aclocal.m4:2480: gl_LOCK is expanded from...
aclocal.m4:939: gt_INTL_SUBDIR_CORE is expanded from...
aclocal.m4:778: AM_INTL_SUBDIR is expanded from...
aclocal.m4:100: AM_GNU_GETTEXT is expanded from...
configure.in:27: the top level
configure.in:27: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_GNU_SOURCE
../../lib/autoconf/specific.m4:331: AC_GNU_SOURCE is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_GNU_SOURCE
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_AIX
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_AIX
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_MINIX
../../lib/autoconf/specific.m4:460: AC_MINIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_MINIX
configure.in:15: warning: macro `AM_PROG_LIBTOOL' not found in library
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:389: AC_USE_SYSTEM_EXTENSIONS is expanded from...
/usr/share/aclocal/lock.m4:29: gl_LOCK_EARLY_BODY is expanded from...
/usr/share/aclocal/lock.m4:22: gl_LOCK_EARLY is expanded from...
/usr/share/aclocal/lock.m4:253: gl_LOCK is expanded from...
/usr/share/aclocal/intl.m4:186: gt_INTL_SUBDIR_CORE is expanded from...
/usr/share/aclocal/intl.m4:25: AM_INTL_SUBDIR is expanded from...
/usr/share/aclocal/gettext.m4:57: AM_GNU_GETTEXT is expanded from...
configure.in:27: the top level
configure.in:27: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_GNU_SOURCE
../../lib/autoconf/specific.m4:331: AC_GNU_SOURCE is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_GNU_SOURCE
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_AIX
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_AIX
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_MINIX
../../lib/autoconf/specific.m4:460: AC_MINIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_MINIX
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:389: AC_USE_SYSTEM_EXTENSIONS is expanded from...
aclocal.m4:2256: gl_LOCK_EARLY_BODY is expanded from...
aclocal.m4:2249: gl_LOCK_EARLY is expanded from...
aclocal.m4:2480: gl_LOCK is expanded from...
aclocal.m4:939: gt_INTL_SUBDIR_CORE is expanded from...
aclocal.m4:778: AM_INTL_SUBDIR is expanded from...
aclocal.m4:100: AM_GNU_GETTEXT is expanded from...
configure.in:27: the top level
configure.in:27: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_GNU_SOURCE
../../lib/autoconf/specific.m4:331: AC_GNU_SOURCE is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_GNU_SOURCE
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_AIX
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_AIX
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_MINIX
../../lib/autoconf/specific.m4:460: AC_MINIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_MINIX
configure.in:27: required file `./config.rpath' not found
Makefile.am:4: AM_GNU_GETTEXT used but `intl' not in SUBDIRS
configure.in:27: required file `./ABOUT-NLS' not found
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:389: AC_USE_SYSTEM_EXTENSIONS is expanded from...
aclocal.m4:2256: gl_LOCK_EARLY_BODY is expanded from...
aclocal.m4:2249: gl_LOCK_EARLY is expanded from...
aclocal.m4:2480: gl_LOCK is expanded from...
aclocal.m4:939: gt_INTL_SUBDIR_CORE is expanded from...
aclocal.m4:778: AM_INTL_SUBDIR is expanded from...
aclocal.m4:100: AM_GNU_GETTEXT is expanded from...
configure.in:27: the top level
configure.in:27: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_GNU_SOURCE
../../lib/autoconf/specific.m4:331: AC_GNU_SOURCE is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_GNU_SOURCE
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_AIX
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_AIX
configure.in:27: warning: AC_COMPILE_IFELSE was called before AC_MINIX
../../lib/autoconf/specific.m4:460: AC_MINIX is expanded from...
configure.in:27: warning: AC_RUN_IFELSE was called before AC_MINIX
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
./configure: line 6543: AM_PROG_LIBTOOL: command not found
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... ranlib
checking for simple visibility declarations... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
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
checking for AIX... no
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
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
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTKMM... configure: error: Package requirements (gtkmm-2.0 >= 2.2.11) were not met:

No package 'gtkmm-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKMM_CFLAGS
and GTKMM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

i went into synaptics did a search for 'gtkmm-2.0' and installed the found packages but it didn't fix it.

---

### Post by taurus on 2008-12-18
Have you installed the -dev package?

---

### Post by simtaalo on 2008-12-18
i selected one in synaptic that said dev but hasn't seemed to have done anything. tried manually with ```
sudo apt-get install gtkmm-2.0-dev
``` but it just returns ```
E: Couldn't find package gtkmm-2.0-dev
```

---

### Post by taurus on 2008-12-18
Which release are you using?  Here's a screenshot of synaptic on my machine.

---

### Post by simtaalo on 2008-12-18
linux mint 5, which is based on 8.04.

here is my synaptic

---

### Post by taurus on 2008-12-18
From your screenshot, you already have libgtkmm-2.4-dev installed on your machine.

---

### Post by simtaalo on 2008-12-18
which is why i'm confused when the command throws the error ```
checking for GTKMM... configure: error: Package requirements (gtkmm-2.0 >= 2.2.11) were not met:

No package 'gtkmm-2.0' found

```

---

### Post by bruce89 on 2008-12-18
GTK-- (mm) went through a ABI change at 2.4. This program needs GTK-- 2.2.11, so you're stuck, as this is not available any more.

---

### Post by simtaalo on 2008-12-18
does anyone know an alternative then for the gaiptek program? trying to get this sorted

[http://ubuntuforums.org/showthread.php?t=1011582](http://ubuntuforums.org/showthread.php?t=1011582)

---

### Post by |{urse on 2009-02-14
sudo apt-get install libgtkmm-2.4-dev

---

