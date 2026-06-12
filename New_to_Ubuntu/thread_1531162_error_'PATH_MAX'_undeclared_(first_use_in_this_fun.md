---
title: "error: 'PATH_MAX' undeclared (first use in this function)"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Fwission on 2010-07-14
```
daniel@daniel-desktop:~$ cd /Desktop/prozgui-2.0.2
bash: cd: /Desktop/prozgui-2.0.2: No such file or directory
daniel@daniel-desktop:~$ cd Desktop/prozgui-2.0.2
daniel@daniel-desktop:~/Desktop/prozgui-2.0.2$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for a BSD compatible install... /usr/bin/install -c
checking for uname... (cached) uname
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking for object suffix... o
checking for executable suffix... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache ./config.cache
checking for strerror in -lcposix... (cached) no
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for inline... (cached) inline
checking for off_t... (cached) yes
checking for size_t... (cached) yes
checking for working alloca.h... (cached) yes
checking for alloca... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking whether we are using the GNU C Library 2.1 or newer... (cached) yes
checking for argz.h... (cached) yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for stddef.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for feof_unlocked... (cached) yes
checking for fgets_unlocked... (cached) yes
checking for getcwd... (cached) yes
checking for getegid... (cached) yes
checking for geteuid... (cached) yes
checking for getgid... (cached) yes
checking for getuid... (cached) yes
checking for mempcpy... (cached) yes
checking for munmap... (cached) yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for setlocale... (cached) yes
checking for stpcpy... (cached) yes
checking for strchr... (cached) yes
checking for strcasecmp... (cached) yes
checking for strdup... (cached) yes
checking for strtoul... (cached) yes
checking for tsearch... (cached) yes
checking for __argz_count... (cached) yes
checking for __argz_stringify... (cached) yes
checking for __argz_next... (cached) yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached) 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... (cached) yes
checking for GNU gettext in libc... (cached) yes
checking for dcgettext... (cached) yes
checking for msgfmt... (cached) no
checking for xgettext... (cached) :
checking for bison... no
checking for catalogs to be installed...  pt_BR nl ro
checking for working const... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking whether struct tm is in sys/time.h or time.h... (cached) time.h
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for unistd.h... (cached) yes
checking for strdup... (cached) yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... (cached) yes
checking for size_t... (cached) yes
checking for socklen_t... (cached) yes
checking for FL/Fl.H... (cached) no
checking for X... (cached) no
checking for pthread_create in -lpthread... (cached) yes
checking for pow in -lm... (cached) yes
checking for XOpenDisplay in -lX11... (cached) no
checking for XdbeQueryExtension in -lXext... (cached) no
checking for XpmCreatePixmapFromData in -lXpm... (cached) no
checking for numericsort in -lfltk... (cached) no
checking for glEnable in -lGL... (cached) no
checking for numericsort in -lfltk... no
creating ./config.status
creating Makefile
creating src/Makefile
creating intl/Makefile
creating po/Makefile.in
creating man/Makefile
creating config.h
config.h is unchanged
creating po/POTFILES
creating po/Makefile
configuring in libprozilla
running /bin/sh ./configure  --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for AIX... no
checking for strerror in -lcposix... (cached) no
checking for minix/config.h... (cached) no
checking for gcc option to accept ANSI C... (cached) none needed
checking for a BSD compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking for object suffix... o
checking for executable suffix... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for objdir... .libs
creating libtool
loading cache .././config.cache
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for inline... (cached) inline
checking for off_t... (cached) yes
checking for size_t... (cached) yes
checking for working alloca.h... (cached) yes
checking for alloca... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking whether we are using the GNU C Library 2.1 or newer... (cached) yes
checking for argz.h... (cached) yes
checking for limits.h... (cached) yes
checking for locale.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for stddef.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for feof_unlocked... (cached) yes
checking for fgets_unlocked... (cached) yes
checking for getcwd... (cached) yes
checking for getegid... (cached) yes
checking for geteuid... (cached) yes
checking for getgid... (cached) yes
checking for getuid... (cached) yes
checking for mempcpy... (cached) yes
checking for munmap... (cached) yes
checking for putenv... (cached) yes
checking for setenv... (cached) yes
checking for setlocale... (cached) yes
checking for stpcpy... (cached) yes
checking for strchr... (cached) yes
checking for strcasecmp... (cached) yes
checking for strdup... (cached) yes
checking for strtoul... (cached) yes
checking for tsearch... (cached) yes
checking for __argz_count... (cached) yes
checking for __argz_stringify... (cached) yes
checking for __argz_next... (cached) yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached) 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... (cached) yes
checking for GNU gettext in libc... (cached) yes
checking for dcgettext... (cached) yes
checking for msgfmt... (cached) no
checking for gmsgfmt... (cached) no
checking for xgettext... (cached) no
found msgfmt program is not GNU msgfmt; ignore it
checking for bison... no
checking for catalogs to be installed...  pt_BR ro nl
checking for pthread_create in -lpthread... (cached) yes
checking for gethostent... (cached) yes
checking for setsockopt... (cached) yes
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking for stdio.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for ctype.h... (cached) yes
checking for errno.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/socket.h... (cached) yes
checking for netinet/in.h... (cached) yes
checking for arpa/inet.h... (cached) yes
checking for netdb.h... (cached) yes
checking for pthread.h... (cached) yes
checking for memory.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for time.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for pwd.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for assert.h... (cached) yes
checking for working const... (cached) yes
checking for size_t... (cached) yes
checking for socklen_t... (cached) yes
checking for vprintf... (cached) yes
checking for select... (cached) yes
checking for socket... (cached) yes
checking for strdup... (cached) yes
checking for strerror... (cached) yes
checking for strtol... (cached) yes
checking for strncasecmp... (cached) yes
checking for snprintf... (cached) yes
checking for vsnprintf... (cached) yes
checking for __snprintf... (cached) no
checking for __vsnprintf... (cached) yes
checking for strchr... (cached) yes
checking for strrchr... (cached) yes
checking for which type of gethostbyname_r... (cached) six
creating ./config.status
creating Makefile
creating docs/Makefile
creating src/Makefile
creating intl/Makefile
creating po/Makefile.in
creating config.h
config.h is unchanged
creating po/POTFILES
creating po/Makefile
daniel@daniel-desktop:~/Desktop/prozgui-2.0.2$ make
make  all-recursive
make[1]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2'
Making all in libprozilla
make[2]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla'
make  all-recursive
make[3]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla'
Making all in intl
make[4]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/intl'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/intl'
Making all in po
make[4]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/po'
PATH=../src:$PATH : --default-domain=libprozilla --directory=.. \
	  --add-comments --keyword=_ --keyword=N_ \
	  --files-from=./POTFILES.in \
	&& test ! -f libprozilla.po \
	   || ( rm -f ./libprozilla.pot \
		&& mv libprozilla.po ./libprozilla.pot )
make[4]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/po'
Making all in docs
make[4]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/docs'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/docs'
Making all in src
make[4]: Entering directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..   -DLOCALEDIR=\"/usr/local/share/locale\"    -Wall -O2 -D_REENTRANT -c download.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -Wp,-MD,.deps/download.pp -c download.c  -fPIC -o .libs/download.o
download.c: In function 'proz_download_init':
download.c:55: error: 'PATH_MAX' undeclared (first use in this function)
download.c:55: error: (Each undeclared identifier is reported only once
download.c:55: error: for each function it appears in.)
download.c:41: warning: unused variable 'attr'
download.c: In function 'proz_download_setup_connections_no_ftpsearch':
download.c:121: error: 'PATH_MAX' undeclared (first use in this function)
download.c: In function 'proz_download_delete_dl_files':
download.c:617: error: 'PATH_MAX' undeclared (first use in this function)
download.c:617: warning: unused variable 'buf'
download.c: In function 'download_join_downloads':
download.c:685: error: 'PATH_MAX' undeclared (first use in this function)
download.c:685: warning: unused variable 'out_file_name'
download.c: In function 'cleanup_joining_thread':
download.c:1012: error: 'PATH_MAX' undeclared (first use in this function)
download.c:1012: warning: unused variable 'out_file_name'
download.c: In function 'proz_download_target_exist':
download.c:1126: error: 'PATH_MAX' undeclared (first use in this function)
download.c:1126: warning: unused variable 'out_file_name'
download.c: In function 'proz_download_delete_target':
download.c:1158: error: 'PATH_MAX' undeclared (first use in this function)
download.c:1158: warning: unused variable 'out_file_name'
make[4]: *** [download.lo] Error 1
make[4]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla'
make[2]: *** [all-recursive-am] Error 2
make[2]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2/libprozilla'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daniel/Desktop/prozgui-2.0.2'
make: *** [all-recursive-am] Error 2
daniel@daniel-desktop:~/Desktop/prozgui-2.0.2$ 
```

I do what the instructions tell me to do but get this error. I tried to google the solution but none of them worked. This also seems to happen with any program I try to install this way. Any help would be appreciated because I'm not only new to Ubuntu but new to the forum as well.

---

