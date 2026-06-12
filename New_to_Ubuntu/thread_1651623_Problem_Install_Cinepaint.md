---
title: "Problem Install Cinepaint"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by DMKryl on 2010-12-23
Hi i've trying to install cinepaint but it keeps sending me error message here is the output TIA

```
kryl@Sasha:~/Desktop/cinep$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
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
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether byte ordering is bigendian... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes

PKG_CONFIG_PATH =

checking fd_set and sys/select... yes
checking for yywrap in -lfl... no
none
checking for pthread_create in -lpthread... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-config... no
configure: WARNING:
*** Check for glib-config failed.
*** You can download Glib from http://www.gtk.org/  .
*** As well check if the glib-devel or similiar package is installed on your
*** distribution.
checking for inline definition in glibconfig.h... no
checking for inline... inline
checking for gtk-config... no
checking for GTK - version >= 1.2.8... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: WARNING: Test for GTK failed. See the file 'INSTALL' for help.
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
checking for catalogs to be installed...  ca cs da de el en_GB es fi fr ga gl hu hr it ja ko lt nl nn no pl pt pt_BR ro ru sk sl sv tr uk zh_CN zh_TW
checking for TIFF support... checking for TIFFOpen in -ltiff... yes
checking tiff.h usability... yes
checking tiff.h presence... yes
checking for tiff.h... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for pkg-config... /usr/bin/pkg-config
Package OpenEXR was not found in the pkg-config search path.
Perhaps you should add the directory containing `OpenEXR.pc'
to the PKG_CONFIG_PATH environment variable
No package 'OpenEXR' found
checking for openexr support... checking OpenEXR/half.h usability... no
checking OpenEXR/half.h presence... no
checking for OpenEXR/half.h... no
configure: WARNING:
*** OpenEXR dev header half.h not found
*** install OpenEXR and development packages or
*** download from http://www.openexr.org 
checking for JPEG support... checking for jinit_memory_mgr in -ljpeg... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libpng... (version 1.2.44) yes
checking for pkg-config... /usr/bin/pkg-config
checking for lcms >= 1.16... yes (version 1.18)
checking for XmuClientWindow in -lXmu... yes
checking X11/Xmu/WinUtil.h usability... yes
checking X11/Xmu/WinUtil.h presence... yes
checking for X11/Xmu/WinUtil.h... yes
checking for pkg-config... /usr/bin/pkg-config
try gutenprintui
checking for gutenprint >= 5.0.0... Package gutenprintui was not found in the pkg-config search path.
Perhaps you should add the directory containing `gutenprintui.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gutenprintui' found
expr: syntax error
configure: WARNING:
*** libgutenprint version  is too old or not available.
*** You need at least version 5.0.0 .
configure: WARNING:
*** Check for libgutenprint failed. Try setting the PKG_CONFIG_PATH variable.
*** You may download it from
*** http://gutenprint.sourceforge.net/ . Take an developers release.
*** They are numberd beginning with 5.0.0 .
*** You can build without printing support by passing
*** --disable-print to configure (but you won't be able to print then).
checking for oyranos-config... no
configure: WARNING:
*** Check for oyranos-config failed.
*** You can download Oyranos from http://www.oyranos.org/  .
checking for fltk-config... /usr/bin/fltk-config
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking whether shmctl IPC_RMID allowes subsequent attaches... no
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for python... /usr/bin/python
checking for Python prefix... /usr
checking for Python exec-prefix... /usr
checking for Python version... python2.6
checking for Python header files... -I/usr/include/python2.6 -I/usr/lib/python2.6/config
checking for Python library... -L/usr/lib/python2.6/config
checking fltk dependend plug-ins ... yes "bracketing_to_hdr" "collect" "pdf"
checking thread dependend plug-ins ... yes "icc_examin"
checking flex dependend plug-ins ... no FLEX dependent plug-ins will be build (iol,...)
checking for rpm... /usr/bin/rpm
configure: creating ./config.status
config.status: creating Makefile
config.status: creating user_install
config.status: creating gimprc
config.status: creating gimprc_user
config.status: creating cinepainttool
config.status: creating cinepaint-gtk.pc
config.status: creating cinepaint.spec
config.status: creating lib/version.h
config.status: creating lib/Makefile
config.status: creating lib/wire/Makefile
config.status: creating lib/fl_i18n/Makefile
config.status: creating libgimp/Makefile
config.status: creating libgimp/gimpintl.h
config.status: creating libhalf/Makefile
config.status: creating plug-ins/Makefile
config.status: creating plug-ins/blur/Makefile
config.status: creating plug-ins/bmp/Makefile
config.status: creating plug-ins/bracketing_to_hdr/Makefile
config.status: creating plug-ins/bracketing_to_hdr/br_core/Makefile
config.status: creating plug-ins/bracketing_to_hdr/FL_adds/Makefile
config.status: creating plug-ins/bracketing_to_hdr/gui/Makefile
config.status: creating plug-ins/bracketing_to_hdr/jhead/Makefile
config.status: creating plug-ins/cineon/Makefile
config.status: creating plug-ins/collect/Makefile
config.status: creating plug-ins/compose/Makefile
config.status: creating plug-ins/dbbrowser/Makefile
config.status: creating plug-ins/decompose/Makefile
config.status: creating plug-ins/dicom/Makefile
config.status: creating plug-ins/edge/Makefile
config.status: creating plug-ins/fits/Makefile
config.status: creating plug-ins/gauss_rle/Makefile
config.status: creating plug-ins/gbr/Makefile
config.status: creating plug-ins/gifload/Makefile
config.status: creating plug-ins/hdr/Makefile
config.status: creating plug-ins/icc_examin/Makefile
config.status: creating plug-ins/iff/Makefile
config.status: creating plug-ins/iol/Makefile
config.status: creating plug-ins/iol/examples/Makefile
config.status: creating plug-ins/jpeg/Makefile
config.status: creating plug-ins/mblur/Makefile
config.status: creating plug-ins/median/Makefile
config.status: creating plug-ins/minimum/Makefile
config.status: creating plug-ins/noisify/Makefile
config.status: creating plug-ins/openexr/Makefile
config.status: creating plug-ins/pic/Makefile
config.status: creating plug-ins/pdf/Makefile
config.status: creating plug-ins/png/Makefile
config.status: creating plug-ins/pnm/Makefile
config.status: creating plug-ins/print/Makefile
config.status: creating plug-ins/psd/Makefile
config.status: creating plug-ins/psd_save/Makefile
config.status: creating plug-ins/pygimp/Makefile
config.status: creating plug-ins/pygimp/doc/Makefile
config.status: creating plug-ins/pygimp/plug-ins/Makefile
config.status: creating plug-ins/script-fu/Makefile
config.status: creating plug-ins/script-fu/scripts/Makefile
config.status: creating plug-ins/rawphoto/Makefile
config.status: creating plug-ins/retinex/Makefile
config.status: creating plug-ins/rotate/Makefile
config.status: creating plug-ins/screenshot/Makefile
config.status: creating plug-ins/sgi/Makefile
config.status: creating plug-ins/sharpen/Makefile
config.status: creating plug-ins/snoise/Makefile
config.status: creating plug-ins/sobel/Makefile
config.status: creating plug-ins/spread/Makefile
config.status: creating plug-ins/tga/Makefile
config.status: creating plug-ins/tiff/Makefile
config.status: creating plug-ins/unsharp/Makefile
config.status: creating plug-ins/xwd/Makefile
config.status: creating po/Makefile.in
config.status: creating po-plug-ins/Makefile.in
config.status: creating po-plug-ins/Makefile
config.status: creating po-script-fu/Makefile.in
config.status: creating po-script-fu/Makefile
config.status: creating app/Makefile
config.status: creating app/depth/Makefile
config.status: creating data/Makefile
config.status: creating data/brushes/Makefile
config.status: creating data/curves/Makefile
config.status: creating data/gradients/Makefile
config.status: creating data/palettes/Makefile
config.status: creating data/patterns/Makefile
config.status: creating lib/config.h
config.status: lib/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default commands
configure: configuring in plug-ins/icc_examin/icc_examin
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.

################################################################
#                                                              #
        Welcome to ICC Examin Version 0.43 configurator
#                                                              #
#                       Configuration                          #

Linux system            detected
Ubuntu 10.10
32-bit system           detected
no Oyranos found
littleCMS 1.18          detected
X11                     detected
X VidMode extension not found in /usr/X11R6/include/X11/extensions/xf86vmode.h or
/usr/include/X11/extensions/xf86vmode.h
X Xinerama              detected
libXpm is available
libXext is available
FTGL      2.1.3~rc5         detected
FLTK 1.1.10              detected
PNG 1.2.44               detected
libdl is available

                        detected
Gettext                 detected
translations available: de eo fr
local CinePaint 0.22-1  detected


generated icc_examin.spec from icc_examin.spec.in
prefix =                /usr/local

################################################################
#                       Configuration                          #
prefix          =       /usr/local
exec_prefix     =       /usr/local
bindir          =       /usr/local/bin
sbindir         =       /usr/local/sbin
libdir          =       /usr/local/lib
includedir      =       /usr/local/include
datadir         =       /usr/local/share
mandir          =       /usr/local/share/man
pixmapdir       =       /usr/local/share/pixmaps
desktopdir      =       /usr/local/share/applications
INCL            :       INCL=-I$(includedir) -I/usr/X11R6/include -I. -I/usr/include/g++ -I/usr/include
CFLAGS          =        $(INCL)
CXXFLAGS        =        $(INCL)
LDFLAGS         =        -L.
################################################################



preparing Makefile in ./
preparing Makefile in fl_i18n/
schaue nach Abhaengikeiten ...

=================================================================
              Configuration Results

GTK CinePaint Version 0.22-1


General dependencies:
./configure: line 29441: gtk-config: command not found
   Gtk1 toolkit                 yes    
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.18
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.44
   Jpeg plug-in:                yes
   Print plug-in:               no
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     no
=================================================================

configure: error: !!! An ERROR occured !!!
    Please check the above messages to see why.
    For bug reports please include the complete above output.
```

---

### Post by scorchgeek on 2010-12-23
It appears you are missing some dependencies...try reading the README or INSTALL file that came in the package and see what you need to install. The script certainly wasn't too specific, though...

The line ```
./configure: line 29441: gtk-config: command not found
``` also looks a bit suspicious, although I don't know exactly how to fix it.

---

### Post by DMKryl on 2010-12-23
Nothing came in the readme or install but in the webpage i found this commands

sudo apt-get install gcc automake g++ libfltk1.1-dev libgtk2.0-dev zlib1g-dev libjpeg62-dev libpng12-dev libtiff4-dev libopenexr-dev libxpm-dev libgutenprint-dev libgutenprintui2-dev liblcms1-dev pkg-config ftgl-dev libxmu-dev libxxf86vm-dev flex python-dev libtool

already tried but still gives me errors

---

### Post by khelben1979 on 2010-12-23
Try with another version of [Cinepaint]("http://en.wikipedia.org/wiki/Cinepaint").

---

### Post by DMKryl on 2010-12-23
Well i tried to search in the software center and synaptic but i couldn't find anything, i have found a page with debs packages but it ask me for a Dependency is not satisfiable: libglib1.2 (>= 1.2.0) but in synaptic i have installed 2.26 :S

[http://mirrors.xmission.com/ubuntu/pool/universe/c/cinepaint/](http://mirrors.xmission.com/ubuntu/pool/universe/c/cinepaint/)

---

### Post by khelben1979 on 2010-12-23
Regarding libglib1.2 (>= 1.2.0)

That means that it haveto accept libglib higher than 1.2. Are you sure you got the libglib2.26-dev? Since you do need the *-dev archives to build the source.

---

### Post by DMKryl on 2010-12-23
yes, unless is the libglibmm, atached screenshot

---

### Post by khelben1979 on 2010-12-23
There is no binary package of Cinepaint which works for you?

---

### Post by DMKryl on 2010-12-24
No they keep asking me for the libglib1.2

---

### Post by lkraemer on 2010-12-25
One of your errors is:
```

checking for glib-config... no
configure: WARNING:
*** Check for glib-config failed.
*** You can download Glib from http://www.gtk.org/  .
*** As well check if the glib-devel or similiar package is installed on your
*** distribution.
checking for inline definition in glibconfig.h... no
checking for inline... inline
checking for gtk-config... no
checking for GTK - version >= 1.2.8... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: WARNING: Test for GTK failed. See the file 'INSTALL' for help.

```
glib-config, glib-devel, & glibcongfig.h were not found/located.
See the file 'INSTALL' for help.

Also make sure you have build-essential and the linux headers installed.


Typically you need to install build-essential, and the headers for the
kernel you are running, if you are going to compile code.
```

uname -r

```
will tell you the kernel you are currently running.
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install the software needed to compile your code.


TYPICAL COMPILE STEPS: (from within your source directory)
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
"make clean" won't remove anything on the first compile, but will clean up
on a successive compile.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

lk

---

### Post by DMKryl on 2010-12-29
> will tell you the kernel you are currently running.
Code:
sudo apt-get install build-essential linux-headers-$(uname -r)
It has the latest headers, i've try the make clean but it make no difference, so i finally gave up installing this program thank you so much for your help.

---

### Post by Ultra Cronic on 2011-12-03
> **DMKryl said:**
> Well i tried to search in the software center and synaptic but i couldn't find anything, i have found a page with debs packages but it ask me for a Dependency is not satisfiable: libglib1.2 (>= 1.2.0) but in synaptic i have installed 2.26 :S

[http://mirrors.xmission.com/ubuntu/pool/universe/c/cinepaint/](http://mirrors.xmission.com/ubuntu/pool/universe/c/cinepaint/)


Just like all the other links people post out here the link is dead, the project personnel emptied the contents , I swear this whole thing is all blab and no produce. If the big mongers of cyberland would do a search for any web page that mentions cinepaint and tear it down, they would be doing the linux community a big favor.
   The error with the statement "oyranos" in it was the one that led me on a 12 hour whirlwind of dependency searches and 90% of the repositories and web links where 404, deeming this whole cinepaint thing a fragment of someones wild imagination.
The only alternative is to install an older os setup that includes cinepaint such as Startcom linux, but if I abandoned every os of linux at the first little booger that I run into I will never get to learn anything useful. How about the project guys writing their own code and stop relying on other peoples work, sounds like windows to me, or is that foundation molasses? Come on!! what ever was in oyranos can be re-written and included in the tar ball, 
    It's a dependency nightmare this cinepaint is. And the arrogance of not acknowledging ubuntu's existence is a real stink.:(:P

---

### Post by Ultra Cronic on 2011-12-03
> **lkraemer said:**
> One of your errors is:
[code]
checking for glib-config... no
configure: WARNING:
*** Check for glib-config failed.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

lk

Snippet2save;
[lkraemer]("http://ubuntuforums.org/member.php?u=365139") Why couldn't all the other people that paste the command lines do as good a job as you did, At least your addition of the term  make clean witch was NOT included in all the other dudes out there posting lines made the difference. Now as my luck would have it, I clicked on the ICON in the 
MultiMedia/ Video Production folder and as usual the program refuses to open. Maybe I need a reboot?  Whatever but at least your instructions got more action. 
I noticed allot of warnings in the lines scrolling up during the build so I am sure the proggy is hosed. but thanks anyway.

---

