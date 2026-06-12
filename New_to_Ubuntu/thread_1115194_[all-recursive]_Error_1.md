---
title: "[all-recursive] Error 1"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by 0ddFox on 2009-04-03
I've been trying to compile Screem and only recently got the ./configure to make all of the files; but, when I try to 'make' it gives the [all-recursive error 1:

> 
oddfox@etpc:~/screem$ sudo make
make  all-recursive
make[1]: Entering directory `/home/oddfox/screem'
Making all in po
make[2]: Entering directory `/home/oddfox/screem/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/oddfox/screem/po'
Making all in libegg
make[2]: Entering directory `/home/oddfox/screem/libegg'
Making all in util
make[3]: Entering directory `/home/oddfox/screem/libegg/util'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/oddfox/screem/libegg/util'
Making all in recent-files
make[3]: Entering directory `/home/oddfox/screem/libegg/recent-files'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DEGG_COMPILATION    -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/libglade-2.0 -I/usr/include/gtkhtml-2.0 -I/usr/include/libgnomeprint-2.2 -I/usr/include/libgnomeprintui-2.2 -I/usr/include/gtksourceview-1.0 -I/usr/include/gnome-menus   -Wall -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -DGNOMEUI_DISABLE_DEPRECATED -g -O2 -MT egg-recent-view.lo -MD -MP -MF ".deps/egg-recent-view.Tpo" -c -o egg-recent-view.lo egg-recent-view.c; \
	then mv -f ".deps/egg-recent-view.Tpo" ".deps/egg-recent-view.Plo"; else rm -f ".deps/egg-recent-view.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DEGG_COMPILATION -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/libglade-2.0 -I/usr/include/gtkhtml-2.0 -I/usr/include/libgnomeprint-2.2 -I/usr/include/libgnomeprintui-2.2 -I/usr/include/gtksourceview-1.0 -I/usr/include/gnome-menus -Wall -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -DGNOMEUI_DISABLE_DEPRECATED -g -O2 -MT egg-recent-view.lo -MD -MP -MF .deps/egg-recent-view.Tpo -c egg-recent-view.c  -fPIC -DPIC -o .libs/egg-recent-view.o
In file included from egg-recent-view.c:28:
egg-recent-view.h:33: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'egg_recent_view_get_type'
egg-recent-view.c:32: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'egg_recent_view_get_type'
egg-recent-view.c: In function 'egg_recent_view_get_model':
egg-recent-view.c:58: warning: implicit declaration of function 'egg_recent_view_get_type'
make[3]: *** [egg-recent-view.lo] Error 1
make[3]: Leaving directory `/home/oddfox/screem/libegg/recent-files'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/oddfox/screem/libegg'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/oddfox/screem'
make: *** [all] Error 2


I've posted the configure log too because something might be going wrong there, but I'm unable to really tell.

Here's the ./configure log (I'm not sure if something is going wrong there, because I've read around and it seems my error might come from not executing 'sudo make' but I've tried that and had no luck. I figure it might be something wrong during configuration. Here's that log too:

> oddfox@etpc:~/screem$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking whether to build static libraries... no
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.29... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.5.6... yes (version 2.18.2)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SCREEM... yes
checking for GNOMEMENU... yes
checking for DBUS... yes
checking for EGG... yes
checking for CROCO... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for mkdir... yes
checking for strsignal... yes
checking for strerror... yes
checking for memcpy... yes
checking for strstr... yes
checking for fnmatch... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for strings.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for stdlib.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for off_t... yes
checking for long... yes
checking size of long... 4
checking for off_t... (cached) yes
checking size of off_t... 4
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  az cs da de el es fr it ja ko nb no pl pt_BR ru rw sk sv tr uk vi zh_CN
checking for scrollkeeper-config... /usr/bin/scrollkeeper-config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libegg/Makefile
config.status: creating libegg/recent-files/Makefile
config.status: creating libegg/util/Makefile
config.status: creating libegg/toolbar-editor/Makefile
config.status: creating gdl/Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating glade/Makefile
config.status: creating ui/Makefile
config.status: creating po/Makefile.in
config.status: creating plugins/Makefile
config.status: creating plugins/screem-plugin.pc
config.status: creating plugins/colourWizard/Makefile
config.status: creating plugins/entityWizard/Makefile
config.status: creating plugins/linkWizard/Makefile
config.status: creating plugins/tableWizard/Makefile
config.status: creating plugins/ssiWizard/Makefile
config.status: creating plugins/formWizard/Makefile
config.status: creating plugins/uploadWizard/Makefile
config.status: creating plugins/css-wizard/Makefile
config.status: creating plugins/object-wizard/Makefile
config.status: creating resources/Makefile
config.status: creating resources/Applets/Makefile
config.status: creating resources/Images/Makefile
config.status: creating resources/Javascript/Makefile
config.status: creating resources/PHP3/Makefile
config.status: creating resources/HTML/Makefile
config.status: creating resources/Templates/Makefile
config.status: creating splash/Makefile
config.status: creating docs/Makefile
config.status: creating docs/C/Makefile
config.status: creating docs/C/figures/Makefile
config.status: creating pixmaps/Makefile
config.status: creating hints/Makefile
config.status: creating dtd/Makefile
config.status: creating data/Makefile
config.status: creating data/mime/Makefile
config.status: creating data/tagtrees/Makefile
config.status: creating helpers/Makefile
config.status: creating helpers/Tidy/Makefile
config.status: creating helpers/browsers/Makefile
config.status: creating helpers/browsers-remote/Makefile
config.status: creating tests/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing default commands


Configuration:
	Source code location:			 .
	Compiler:				 gcc

	Install location:			 /usr/local

Type make to build Screem.



I made sure GCC was already installed, etc. So...I'm not sure what's wrong and i'm a n00b at compiling.

Thanks.

0ddfox

---

### Post by Elfy on 2009-04-03
Did you know it is in the repos? Assuming that you are trying to install

screem - A GNOME website development environment

You can install it from there

```
sudo apt-get install screem
```

Just a fyi - if you had used code instead of quote then the config log would look a lot smaller :)

---

