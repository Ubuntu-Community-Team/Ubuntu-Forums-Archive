---
title: "How can I tell if I successfully installed the Driver?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by teotuf on 2009-01-20
I've only used Ubuntu for 2 days, since my wonderful recovery dvds from sony does not actually recover the computer... and the only thing windows I can install on this computer is windows 7 beta, which isn't bad, but does have a time limit...

I'm using Sony Vaio vgn-fw140e, with a intel 4500mhd graphics card.

Now the reason I'm doing this especially since I'm really inexperienced with Ubuntu is that:
1. The driver that came with Ubuntu has a bug with Sony Vaio so it does not load onto the desktop server ([https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292))

2. I have installed Ubuntu successfully using safe graphics mode from live cd, and then installed the driver posted on [http://www.uluga.ubuntuforums.org/showthread.php?t=1023801](http://www.uluga.ubuntuforums.org/showthread.php?t=1023801)
However, it has incompatibilities when I try to run games in Wine (anything full screen freezes or restarts the computer, which according to the wiki for Wine, is a graphics driver incompatibility)

So I'm trying to apply the fix to the new driver and compile it myself.
----------------------------------------------------------------------------------
I downloaded "xf86-video-intel 2.6.0 release" from [http://intellinuxgraphics.org/2008Q4.html](http://intellinuxgraphics.org/2008Q4.html)
Unzipped into "/home/bill/Desktop/intel" (changed the folder name to intel)
Applied the patch "Make sure h & vblank end come *after* h & vsync end" to "i830_bios.c" from [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)

and in terminal, I ran:
```
sudo -i
cd /home/bill/Desktop/intel
./configure
(now I installed a bunch of needed dependencies from Synaptic, basically searched for whatever it said I was missing from the terminal output)
and after a billion years trying to figure those out, this is what I get:
[CODE]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gfortran option to produce PIC... -fPIC
checking if gfortran PIC flag -fPIC works... yes
checking if gfortran static flag -static works... yes
checking if gfortran supports -c -o file.o... yes
checking whether the gfortran linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
checking for bash... /bin/bash
checking if libtool sucks... yup, it does
checking if dolt supports this host... yes, replacing libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for intel-gen4asm... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for UXA... yes
checking for ANSI C header files... (cached) yes
checking whether to include DRI support... checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking for /usr/include/xorg/damage.h... yes
checking whether to include DRI support... yes
checking for xf86Modes.h... yes
checking whether XSERVER_LIBPCIACCESS is declared... yes
checking for PCIACCESS... yes
configure: X server has new mode code
checking whether xf86RotateFreeShadow is declared... no
checking for DRM... yes
checking for DRI... yes
checking for DRM_MODE... yes
checking for XVMCLIB... no
checking for XEXT... yes
checking whether to include XvMC support... no
checking if xorg-macros used to generate configure is at least 1.1... yes, 1.2.0
checking for NONE/share/sgml/X11/defs.ent... no
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
checking Whether to build documentation... no
checking Whether to build pdf documentation... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating uxa/Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating src/bios_reader/Makefile
config.status: creating src/ch7017/Makefile
config.status: creating src/ch7xxx/Makefile
config.status: creating src/ivch/Makefile
config.status: creating src/reg_dumper/Makefile
config.status: creating src/sil164/Makefile
config.status: creating src/tfp410/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
```
And now I do:
make
and I get:
```
make  all-recursive
make[1]: Entering directory `/home/bill/Desktop/intel'
Making all in uxa
make[2]: Entering directory `/home/bill/Desktop/intel/uxa'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/bill/Desktop/intel/uxa'
Making all in src
make[2]: Entering directory `/home/bill/Desktop/intel/src'
make  all-recursive
make[3]: Entering directory `/home/bill/Desktop/intel/src'
Making all in xvmc
make[4]: Entering directory `/home/bill/Desktop/intel/src/xvmc'
make  all-am
make[5]: Entering directory `/home/bill/Desktop/intel/src/xvmc'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/bill/Desktop/intel/src/xvmc'
make[4]: Leaving directory `/home/bill/Desktop/intel/src/xvmc'
Making all in bios_reader
make[4]: Entering directory `/home/bill/Desktop/intel/src/bios_reader'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/bios_reader'
Making all in ch7017
make[4]: Entering directory `/home/bill/Desktop/intel/src/ch7017'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ch7017'
Making all in ch7xxx
make[4]: Entering directory `/home/bill/Desktop/intel/src/ch7xxx'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ch7xxx'
Making all in ivch
make[4]: Entering directory `/home/bill/Desktop/intel/src/ivch'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ivch'
Making all in sil164
make[4]: Entering directory `/home/bill/Desktop/intel/src/sil164'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/sil164'
Making all in tfp410
make[4]: Entering directory `/home/bill/Desktop/intel/src/tfp410'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/tfp410'
Making all in reg_dumper
make[4]: Entering directory `/home/bill/Desktop/intel/src/reg_dumper'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/reg_dumper'
make[4]: Entering directory `/home/bill/Desktop/intel/src'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src'
make[3]: Leaving directory `/home/bill/Desktop/intel/src'
make[2]: Leaving directory `/home/bill/Desktop/intel/src'
Making all in man
make[2]: Entering directory `/home/bill/Desktop/intel/man'
rm -f i810.4
echo .so man4/intel.4 > \
		i810.4
make  all-am
make[3]: Entering directory `/home/bill/Desktop/intel/man'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/bill/Desktop/intel/man'
make[2]: Leaving directory `/home/bill/Desktop/intel/man'
make[2]: Entering directory `/home/bill/Desktop/intel'
make[2]: Leaving directory `/home/bill/Desktop/intel'
make[1]: Leaving directory `/home/bill/Desktop/intel'
```
And finally:
make install
And I get:
```
Making install in uxa
make[1]: Entering directory `/home/bill/Desktop/intel/uxa'
make[2]: Entering directory `/home/bill/Desktop/intel/uxa'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bill/Desktop/intel/uxa'
make[1]: Leaving directory `/home/bill/Desktop/intel/uxa'
Making install in src
make[1]: Entering directory `/home/bill/Desktop/intel/src'
make  install-recursive
make[2]: Entering directory `/home/bill/Desktop/intel/src'
Making install in xvmc
make[3]: Entering directory `/home/bill/Desktop/intel/src/xvmc'
make  install-am
make[4]: Entering directory `/home/bill/Desktop/intel/src/xvmc'
make[5]: Entering directory `/home/bill/Desktop/intel/src/xvmc'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/bill/Desktop/intel/src/xvmc'
make[4]: Leaving directory `/home/bill/Desktop/intel/src/xvmc'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/xvmc'
Making install in bios_reader
make[3]: Entering directory `/home/bill/Desktop/intel/src/bios_reader'
make[4]: Entering directory `/home/bill/Desktop/intel/src/bios_reader'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/bios_reader'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/bios_reader'
Making install in ch7017
make[3]: Entering directory `/home/bill/Desktop/intel/src/ch7017'
make[4]: Entering directory `/home/bill/Desktop/intel/src/ch7017'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'ch7017.la' '/usr/local/lib/xorg/modules/drivers/ch7017.la'
/usr/bin/install -c .libs/ch7017.so /usr/local/lib/xorg/modules/drivers/ch7017.so
/usr/bin/install -c .libs/ch7017.lai /usr/local/lib/xorg/modules/drivers/ch7017.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ch7017'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/ch7017'
Making install in ch7xxx
make[3]: Entering directory `/home/bill/Desktop/intel/src/ch7xxx'
make[4]: Entering directory `/home/bill/Desktop/intel/src/ch7xxx'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'ch7xxx.la' '/usr/local/lib/xorg/modules/drivers/ch7xxx.la'
/usr/bin/install -c .libs/ch7xxx.so /usr/local/lib/xorg/modules/drivers/ch7xxx.so
/usr/bin/install -c .libs/ch7xxx.lai /usr/local/lib/xorg/modules/drivers/ch7xxx.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ch7xxx'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/ch7xxx'
Making install in ivch
make[3]: Entering directory `/home/bill/Desktop/intel/src/ivch'
make[4]: Entering directory `/home/bill/Desktop/intel/src/ivch'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'ivch.la' '/usr/local/lib/xorg/modules/drivers/ivch.la'
/usr/bin/install -c .libs/ivch.so /usr/local/lib/xorg/modules/drivers/ivch.so
/usr/bin/install -c .libs/ivch.lai /usr/local/lib/xorg/modules/drivers/ivch.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/bill/Desktop/intel/src/ivch'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/ivch'
Making install in sil164
make[3]: Entering directory `/home/bill/Desktop/intel/src/sil164'
make[4]: Entering directory `/home/bill/Desktop/intel/src/sil164'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'sil164.la' '/usr/local/lib/xorg/modules/drivers/sil164.la'
/usr/bin/install -c .libs/sil164.so /usr/local/lib/xorg/modules/drivers/sil164.so
/usr/bin/install -c .libs/sil164.lai /usr/local/lib/xorg/modules/drivers/sil164.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/bill/Desktop/intel/src/sil164'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/sil164'
Making install in tfp410
make[3]: Entering directory `/home/bill/Desktop/intel/src/tfp410'
make[4]: Entering directory `/home/bill/Desktop/intel/src/tfp410'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c  'tfp410.la' '/usr/local/lib/xorg/modules/drivers/tfp410.la'
/usr/bin/install -c .libs/tfp410.so /usr/local/lib/xorg/modules/drivers/tfp410.so
/usr/bin/install -c .libs/tfp410.lai /usr/local/lib/xorg/modules/drivers/tfp410.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Leaving directory `/home/bill/Desktop/intel/src/tfp410'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/tfp410'
Making install in reg_dumper
make[3]: Entering directory `/home/bill/Desktop/intel/src/reg_dumper'
make[4]: Entering directory `/home/bill/Desktop/intel/src/reg_dumper'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/bill/Desktop/intel/src/reg_dumper'
make[3]: Leaving directory `/home/bill/Desktop/intel/src/reg_dumper'
make[3]: Entering directory `/home/bill/Desktop/intel/src'
make[4]: Entering directory `/home/bill/Desktop/intel/src'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/xorg/modules/drivers" || /bin/mkdir -p "/usr/local/lib/xorg/modules/drivers"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'intel_drv.la' '/usr/local/lib/xorg/modules/drivers/intel_drv.la'
/usr/bin/install -c .libs/intel_drv.so /usr/local/lib/xorg/modules/drivers/intel_drv.so
/usr/bin/install -c .libs/intel_drv.lai /usr/local/lib/xorg/modules/drivers/intel_drv.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/xorg/modules/drivers
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xorg/modules/drivers

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
(cd /usr/local/lib/xorg/modules/drivers && rm -f i810_drv.so && ln -s intel_drv.so i810_drv.so)
make[4]: Leaving directory `/home/bill/Desktop/intel/src'
make[3]: Leaving directory `/home/bill/Desktop/intel/src'
make[2]: Leaving directory `/home/bill/Desktop/intel/src'
make[1]: Leaving directory `/home/bill/Desktop/intel/src'
Making install in man
make[1]: Entering directory `/home/bill/Desktop/intel/man'
rm -f i810.4
echo .so man4/intel.4 > \
		i810.4
make  install-am
make[2]: Entering directory `/home/bill/Desktop/intel/man'
make[3]: Entering directory `/home/bill/Desktop/intel/man'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man4" || /bin/mkdir -p "/usr/local/share/man/man4"
 /usr/bin/install -c -m 644 'intel.4' '/usr/local/share/man/man4/intel.4'
 /usr/bin/install -c -m 644 'i810.4' '/usr/local/share/man/man4/i810.4'
make[3]: Leaving directory `/home/bill/Desktop/intel/man'
make[2]: Leaving directory `/home/bill/Desktop/intel/man'
make[1]: Leaving directory `/home/bill/Desktop/intel/man'
make[1]: Entering directory `/home/bill/Desktop/intel'
make[2]: Entering directory `/home/bill/Desktop/intel'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/bill/Desktop/intel'
make[1]: Leaving directory `/home/bill/Desktop/intel'
```
[/CODE]
Now after I did all that, I went in nano and changed xorg.conf driver to "intel"

However, when I log out and log back in, it says "intel" driver is not found.

Am I doing anything wrong?

I've done some research, so I'm crossing my finger for not to be taken as a lazy noob who expect everything to be done for him, but this is as far as I could get...

Thanks a lot for reading, and hopefully I can get some help! =(


P.S. In the intel graphics page, there was the step ```
Once the new driver is installed, make sure your xorg.conf file (often in /etc/X11/) points at the new driver, which should be called "intel" or "i810" assuming the "make install" step created the appropriate symlinks.
```
How do I check if the said symlinks were actually successfully created?

---

### Post by hyper_ch on 2009-01-20
intel should be working out of the box :(

install looks ok IMHO

---

### Post by teotuf on 2009-01-20
> intel should be working out of the box 
The one that came with Ubuntu has a bug with Sony FW series, so it does not display the actual desktop unless a external monitor is hooked up ([https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)).

The fix given in [http://www.uluga.ubuntuforums.org/sh....php?t=1023801](http://www.uluga.ubuntuforums.org/sh....php?t=1023801) does not work with full screen games in Wine.

---

