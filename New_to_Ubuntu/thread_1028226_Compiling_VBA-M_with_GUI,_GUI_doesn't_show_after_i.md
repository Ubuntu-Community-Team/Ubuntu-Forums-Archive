---
title: "Compiling VBA-M with GUI, GUI doesn't show after installing"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by andy_blah on 2009-01-02
This is what ./configure outputs:

```
$ ./configure --enable-gtk=2.4
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for nasm... /usr/bin/nasm
checking for gzopen in -lz... yes
checking for png_create_write_struct in -lpng... yes
checking for pthread_yield in -lpthread... yes
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for egrep... grep -E
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
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking zutil.h usability... no
checking zutil.h presence... no
checking for zutil.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for socklen_t... yes
checking whether byte ordering is bigendian... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.2... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.4 >= 2.0.0 libglademm-2.4 >= 2.1.0... yes
checking GTKMM_CFLAGS... -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libglademm-2.4 -I/usr/lib/libglademm-2.4/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2  
checking GTKMM_LIBS... -lglademm-2.4 -lgtkmm-2.4 -lglade-2.0 -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/gb/Makefile
config.status: creating src/gtk/Makefile
config.status: creating src/gtk/images/Makefile
config.status: creating src/i386/Makefile
config.status: creating src/prof/Makefile
config.status: creating src/sdl/Makefile
config.status: creating win32/Makefile
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
```

I don't see anything wrong in there, when I compiled the first time, typed "vbam" in the terminal and the emulator started, only that it didn't show any GUI, and I opted for that at configure. I removed afterwards the emulator from Synaptic and tried to compile it again (after I typed "make clean" too), but this time when I typed in "vbam", it said that the command was not found. What am I doing wrong here?

---

### Post by ken22 on 2009-01-02
Is says checking for X...no

Are you currently running an X server?

---

### Post by andy_blah on 2009-01-02
I don't know if this answers your question, but I am running GNOME 2.24.1.

---

### Post by ken22 on 2009-01-02
Try ```
sudo apt-get install libx11-dev
```

then try reinstalling vbam

---

### Post by andy_blah on 2009-01-02
```
$ sudo apt-get install libx11-dev

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
libx11-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I would also like to know for future reference if I responded properly to your question in your first reply.

---

### Post by ken22 on 2009-01-02
Gnome runs on top of an X server, so saying you were running Gnome means you must be running an X. That answered my question.

I'll have a look to see if I can find an answer to this problem.

---

### Post by ken22 on 2009-01-02
ok, I think ```
sudo apt-get install xlibs-dev
```

will provide the necessary headers to compile VBA-M. Please try that.

---

### Post by andy_blah on 2009-01-02
```
$ sudo apt-get install xlibs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate

```

Tried also to search over at packages.ubuntu.org, and didn't find anything there :?

---

### Post by ken22 on 2009-01-02
Make sure you have all the repos accessible.

Basically you're looking for a package that provides the header files for the X server so you can use them in your compilation of VBA-M

---

### Post by ken22 on 2009-01-02
Next I'd try```
sudo apt-get install xorg-dev
```

---

### Post by andy_blah on 2009-01-02
Installed xorg-dev, and re-installed VBA-M, and this is the output of ./configure:

```
$ sudo ./configure --enable-gtk=2.4
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for nasm... /usr/bin/nasm
checking for gzopen in -lz... yes
checking for png_create_write_struct in -lpng... yes
checking for pthread_yield in -lpthread... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for egrep... grep -E
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
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking zutil.h usability... no
checking zutil.h presence... no
checking for zutil.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for socklen_t... yes
checking whether byte ordering is bigendian... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.2... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtkmm-2.4 >= 2.0.0 libglademm-2.4 >= 2.1.0... yes
checking GTKMM_CFLAGS... -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libglademm-2.4 -I/usr/lib/libglademm-2.4/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2  
checking GTKMM_LIBS... -lglademm-2.4 -lgtkmm-2.4 -lglade-2.0 -lgiomm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lpangomm-1.4 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/gb/Makefile
config.status: creating src/gtk/Makefile
config.status: creating src/gtk/images/Makefile
config.status: creating src/i386/Makefile
config.status: creating src/prof/Makefile
config.status: creating src/sdl/Makefile
config.status: creating win32/Makefile
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
```

Those two errors are that keep appearning to various source files while make-ing:

```
 warning: deprecated conversion from string constant to &#8216;char*&#8217;

 warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result
```

It still doesn't want to start when typing in "vbam"

---

### Post by ken22 on 2009-01-03
run ```
make uninstall
./configure
make
make install
```

we've solved the X library dependancy at least.

*progress* hurrah.

---

### Post by andy_blah on 2009-01-03
I've did that before, done it again this time, but this time the make process didn't took that much, and was less resource consuming. Still cannot use the vbam command :?

---

### Post by ken22 on 2009-01-04
Try this command

```
gvbam
```

---

### Post by andy_blah on 2009-01-04
That doesn't work either unfortunately, it doesn't appear in Synaptic either ...

---

### Post by ken22 on 2009-01-04
The only reason I can think of that it wouldn't have been in synaptic is if it's not installed.

./configure only prepares for compilation, make only compiles it. make install is what installs it.

You might try the project forum [here]("http://vba-m.ngemu.com/forum/")

---

