---
title: "problem with installing pidgin"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by yakoza on 2009-10-04
hi,there

i'm trying to compile pidgin 2.6.2 from source

when i type ./configure i get these messages

```
naser@naser-desktop:~/app/pidgin-2.6.2$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether to build static libraries... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for working alloca.h... yes
checking for alloca... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr ga gl gu he hi hu hy id it ja ka km kn ko ku lo lt mk mn my_MM nb ne nl nn oc pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv sw ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for inet_ntop... yes
checking for socklen_t... yes
checking for struct sockaddr.sa_len... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... no
no
configure: error:

You must have GLib 2.4.0 or newer development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.

```what's GLib ?
how should i solve this problem ?

sorry for my english :popcorn:
tnx

---

### Post by sisco311 on 2009-10-04
You need to install libglib2.0-dev:
```
sudo apt-get install libglib2.0-dev
```

to satisfy all the builld dependencies:
```
sudo apt-get build-dep pidgin
```

---

### Post by halitech on 2009-10-04
Did you install build-essential first?

Also, why compile it, it should already be installed by default.

---

### Post by yakoza on 2009-10-04
>  Also, why compile it, it should already be installed by default.
yes , by default it is installed but i need the latest version

tnx

---

### Post by yakoza on 2009-10-04
> **sisco311 said:**
> You need to install libglib2.0-dev:
```
sudo apt-get install libglib2.0-dev
```to satisfy all the builld dependencies:
```
sudo apt-get build-dep pidgin
```

i installed libglib2.0-dev

but there is a new problem

> You must have GTK+ 2.4.0 or newer development headers installed to compile
Pidgin.  If you want to build only Finch then specify --disable-gtkui when
running configure.


---

### Post by sisco311 on 2009-10-04
As i sad before, *sudo apt-get build-dep pidgin* should install all the packages you need to compile pidgin.

By the way, pidgin 2.6.1 is in the [ppa repo]("http://www.pidgin.im/download/ubuntu/").

You can download  pidgin 2.6.2  from:  [http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

---

### Post by yakoza on 2009-10-04
> **sisco311 said:**
> As i sad before, *sudo apt-get build-dep pidgin* should install all the packages you need to compile pidgin.

By the way, pidgin 2.6.1 is in the [ppa repo]("http://www.pidgin.im/download/ubuntu/").

You can download  pidgin 2.6.2  from:  [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

tnx for your helping :P

---

