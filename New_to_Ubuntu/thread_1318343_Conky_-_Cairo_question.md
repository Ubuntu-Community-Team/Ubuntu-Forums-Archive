---
title: "Conky - Cairo question"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by merlin_ie on 2009-11-07
Hey all. I'm having a bit of a problem getting the "Conky Rings" in my conky. When I try to compile from source I get the following output from terminal (error in red): 
```
./configure --enable-lua --enable-hddtemp --enable-imlib2 --enable-cairo
[COLOR="Red"]**configure: WARNING: unrecognized options: --enable-cairo**[/COLOR]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
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
checking whether to build static libraries... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... yes
checking for getnameinfo... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for X11... yes
checking for Xext... yes
checking for XDamage... yes
checking for Xft... yes
checking for Imlib2... yes
checking for GLib2... yes
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for sys/stat.h... (cached) yes
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking for alsa/asoundlib.h... (cached) no
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking mcheck.h usability... yes
checking mcheck.h presence... yes
checking for mcheck.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for sys/mount.h... yes
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
checking for calloc... yes
checking for malloc... yes
checking for free... yes
checking for popen... yes
checking for sysinfo... yes
checking for getloadavg... yes
checking for memrchr... yes
checking for strndup... yes
checking for gethostbyname_r... yes
checking for library containing clock_gettime... -lrt
checking for struct statfs.f_fstypename... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for db2x_xsltproc... no
checking for db2x_manxml... no
checking for xsltproc... xsltproc
checking if /usr/bin/ld accepts -O1... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating src/build.h
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
configure: WARNING: unrecognized options: --enable-cairo

conky 1.7.1.1 configured successfully:

 Installing into:   /usr/local
 System config dir: ${prefix}/etc
 C compiler flags:    -I/usr/include/lua5.1         -I/usr/include/freetype2     -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W
 Linker flags:       -Wl,-O1
 Libraries:         -lrt  -lm  -llua5.1    -lX11   -lXext   -lXdamage -lXfixes   -lXft   -lImlib2   -lglib-2.0  

 * X11:
  X11 support:      yes
  XDamage support:  yes
  XDBE support:     yes
  Xft support:      yes

 * Music detection:
  Audacious:        no
  BMPx:             no
  MPD:              yes
  MOC:              yes
  XMMS2:            no

 * General:
  OpenMP:           no
  math:             yes
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  Lua:              yes
  wireless:         no
  IBM:              no
  nvidia:           no
  eve-online:       no
  config-output:    yes
  Imlib2:           yes
  ALSA mixer:       no
  apcupsd:          yes

```

I´ve downloaded the conky-all deb hoping this would fix the cairo error but to no avail. I was just wondering, does it mean the cairo as in "cairo dock"? or am I missing a dependency? Using Ubuntu 9.04. Any help would be greatly appreciated.

---

