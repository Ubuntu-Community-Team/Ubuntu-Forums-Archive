---
title: "Could use some help installing an app from source..."
date: 2009-11-18
forum: New to Ubuntu
---

### Post by djm227 on 2009-11-18
I'm still pretty new to Ubuntu, and this is the first time I have had to do this...so I would really appreciate some help.

The software I need to install is [this]("http://www.nongnu.org/aldo/").  I downloaded the tar.bz2 file and extracted it.  I tried to follow the Install text document but couldn't figure it out.  Here's exactly what I did:

1) I ran ./configure and got this:

>  
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for main in -lao... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking ao/ao.h usability... no
checking ao/ao.h presence... no
checking for ao/ao.h... no
Error! You need to have libao ([www.xiph.org/ao]("http://www.xiph.org/ao")) around.
2) I went to that libao site, downloaded and extracted the files, and ran ./configure on that.  Here's what I got:

> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dlfcn.h... (cached) yes
checking for library containing dlopen... -ldl
checking for pthread_kill in -lpthread... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for mmsystem.h... no
checking for esd-config... no
checking for ESD - version >= 0.2.8... no
*** The esd-config script installed by ESD could not be found
*** If ESD was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESD_CONFIG environment variable to the
*** full path to esd-config.
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking for snd_pcm_channel_params in -lasound... no
checking sys/asoundlib.h usability... no
checking sys/asoundlib.h presence... no
checking for sys/asoundlib.h... no
checking for snd_pcm_open in -lasound... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking for artsc-config... no
checking for X... no
checking for XauFileName in -lXau... no
checking for AuOpenServer in -laudio... no
checking audio/audiolib.h usability... no
checking audio/audiolib.h presence... no
checking for audio/audiolib.h... no
checking for pkg-config... /usr/bin/pkg-config
checking for  libpulse-simple >= 0.9 ... configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating include/Makefile
config.status: creating include/ao/Makefile
config.status: creating include/ao/os_types.h
config.status: creating src/plugins/Makefile
config.status: creating src/plugins/esd/Makefile
config.status: creating src/plugins/oss/Makefile
config.status: creating src/plugins/alsa/Makefile
config.status: creating src/plugins/alsa09/Makefile
config.status: creating src/plugins/sun/Makefile
config.status: creating src/plugins/irix/Makefile
config.status: creating src/plugins/arts/Makefile
config.status: creating src/plugins/macosx/Makefile
config.status: creating src/plugins/nas/Makefile
config.status: creating src/plugins/pulse/Makefile
config.status: creating ao.pc
config.status: executing depfiles commands
3) Not sure what anything above means, whether it worked or not, so I moved on and ran "make".  I got the following:

> 
Making all in src
make[1]: Entering directory `/home/dan/Downloads/libao-0.8.8/src'
Making all in plugins
make[2]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins'
Making all in oss
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/oss'
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../../../include/ao -I../../../include    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_oss.lo -MD -MP -MF .deps/ao_oss.Tpo -c -o ao_oss.lo ao_oss.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../../../include/ao -I../../../include -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_oss.lo -MD -MP -MF .deps/ao_oss.Tpo -c ao_oss.c  -fPIC -DPIC -o .libs/ao_oss.o
mv -f .deps/ao_oss.Tpo .deps/ao_oss.Plo
/bin/bash ../../../libtool --tag=CC   --mode=link gcc  -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -export-dynamic -avoid-version  -o liboss.la -rpath /usr/local/lib/ao/plugins-2 ao_oss.lo  -lpthread -ldl 
rm -fr  .libs/liboss.la .libs/liboss.lai .libs/liboss.so
gcc -shared  .libs/ao_oss.o  -lpthread -ldl  -Wl,-soname -Wl,liboss.so -o .libs/liboss.so
creating liboss.la
(cd .libs && rm -f liboss.la && ln -s ../liboss.la liboss.la)
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/oss'
Making all in esd
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/esd'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/esd'
Making all in arts
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/arts'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/arts'
Making all in alsa
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/alsa'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/alsa'
Making all in alsa09
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/alsa09'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/alsa09'
Making all in sun
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/sun'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/sun'
Making all in irix
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/irix'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/irix'
Making all in macosx
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/macosx'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/macosx'
Making all in nas
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/nas'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/nas'
Making all in pulse
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins/pulse'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins/pulse'
make[3]: Entering directory `/home/dan/Downloads/libao-0.8.8/src/plugins'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins'
make[2]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src/plugins'
make[2]: Entering directory `/home/dan/Downloads/libao-0.8.8/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\"    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT audio_out.lo -MD -MP -MF .deps/audio_out.Tpo -c -o audio_out.lo audio_out.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\" -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT audio_out.lo -MD -MP -MF .deps/audio_out.Tpo -c audio_out.c  -fPIC -DPIC -o .libs/audio_out.o
mv -f .deps/audio_out.Tpo .deps/audio_out.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\"    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_null.lo -MD -MP -MF .deps/ao_null.Tpo -c -o ao_null.lo ao_null.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\" -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_null.lo -MD -MP -MF .deps/ao_null.Tpo -c ao_null.c  -fPIC -DPIC -o .libs/ao_null.o
mv -f .deps/ao_null.Tpo .deps/ao_null.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\"    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_wav.lo -MD -MP -MF .deps/ao_wav.Tpo -c -o ao_wav.lo ao_wav.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\" -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_wav.lo -MD -MP -MF .deps/ao_wav.Tpo -c ao_wav.c  -fPIC -DPIC -o .libs/ao_wav.o
mv -f .deps/ao_wav.Tpo .deps/ao_wav.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\"    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_au.lo -MD -MP -MF .deps/ao_au.Tpo -c -o ao_au.lo ao_au.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\" -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_au.lo -MD -MP -MF .deps/ao_au.Tpo -c ao_au.c  -fPIC -DPIC -o .libs/ao_au.o
mv -f .deps/ao_au.Tpo .deps/ao_au.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" -DPACKAGE_STRING=\"libao\ 0.8.8\" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 -DDLOPEN_FLAG=\(RTLD_NOW\ \|\ RTLD_GLOBAL\) -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\"    -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_raw.lo -MD -MP -MF .deps/ao_raw.Tpo -c -o ao_raw.lo ao_raw.c
 gcc -DPACKAGE_NAME=\"libao\" -DPACKAGE_TARNAME=\"libao\" -DPACKAGE_VERSION=\"0.8.8\" "-DPACKAGE_STRING=\"libao 0.8.8\"" -DPACKAGE_BUGREPORT=\"benjihan@users.sourceforge.net\" -DPACKAGE=\"libao\" -DVERSION=\"0.8.8\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLFCN_H=1 -DHAVE_DLOPEN=1 -DHAVE_LIBPTHREAD=1 "-DDLOPEN_FLAG=(RTLD_NOW | RTLD_GLOBAL)" -DSHARED_LIB_EXT=\".so\" -DSIZEOF_SHORT=2 -DSIZEOF_INT=4 -DSIZEOF_LONG=4 -DHAVE_SYS_SOUNDCARD_H=1 -DX_DISPLAY_MISSING=1 -I. -I../include/ao -I../include -DAO_PLUGIN_PATH=\"/usr/local/lib/ao/plugins-2\" -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -MT ao_raw.lo -MD -MP -MF .deps/ao_raw.Tpo -c ao_raw.c  -fPIC -DPIC -o .libs/ao_raw.o
mv -f .deps/ao_raw.Tpo .deps/ao_raw.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -O20 -ffast-math -D_REENTRANT -fsigned-char -g -O2 -version-info 3:3:1  -o libao.la -rpath /usr/local/lib audio_out.lo config.lo ao_null.lo ao_wav.lo ao_au.lo ao_raw.lo ao_aixs.lo   -lpthread -ldl 
rm -fr  .libs/libao.la .libs/libao.lai .libs/libao.so .libs/libao.so.2 .libs/libao.so.2.1.3
gcc -shared  .libs/audio_out.o .libs/config.o .libs/ao_null.o .libs/ao_wav.o .libs/ao_au.o .libs/ao_raw.o .libs/ao_aixs.o  -lpthread -ldl  -Wl,-soname -Wl,libao.so.2 -o .libs/libao.so.2.1.3
(cd .libs && rm -f libao.so.2 && ln -s libao.so.2.1.3 libao.so.2)
(cd .libs && rm -f libao.so && ln -s libao.so.2.1.3 libao.so)
creating libao.la
(cd .libs && rm -f libao.la && ln -s ../libao.la libao.la)
make[2]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src'
make[1]: Leaving directory `/home/dan/Downloads/libao-0.8.8/src'
Making all in include
make[1]: Entering directory `/home/dan/Downloads/libao-0.8.8/include'
Making all in ao
make[2]: Entering directory `/home/dan/Downloads/libao-0.8.8/include/ao'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dan/Downloads/libao-0.8.8/include/ao'
make[2]: Entering directory `/home/dan/Downloads/libao-0.8.8/include'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/dan/Downloads/libao-0.8.8/include'
make[1]: Leaving directory `/home/dan/Downloads/libao-0.8.8/include'
Making all in doc
make[1]: Entering directory `/home/dan/Downloads/libao-0.8.8/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dan/Downloads/libao-0.8.8/doc'
make[1]: Entering directory `/home/dan/Downloads/libao-0.8.8'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/dan/Downloads/libao-0.8.8'

I pretty much left it there....didn't seem like it worked and I have NO idea how to get it work. I'm not even sure what the commands are that I did do....I was just following the Install text.  Like I said, any help for this lost noob would be much appreciated.

Thanks a lot.

---

### Post by Cheesemill on 2009-11-18
Why on earth would you want to compile it from source when it's in the repositories?

```
sudo apt-get install aldo
```

---

### Post by QIII on 2009-11-18
Not sure which version of Ubuntu you are running, but ALDO is available in the Karmic repos.

---

### Post by QIII on 2009-11-18
Aw, cheesemill -- give an old fart a break!

Fingers aren't so fast, bifocals make it hard to see the keyboard...

---

### Post by sandyd on 2009-11-18
> **djm227 said:**
> I'm still pretty new to Ubuntu, and this is the first time I have had to do this...so I would really appreciate some help.

The software I need to install is [this]("http://www.nongnu.org/aldo/").  I downloaded the tar.bz2 file and extracted it.  I tried to follow the Install text document but couldn't figure it out.  Here's exactly what I did:

1) I ran ./configure and got this:

2) I went to that libao site, downloaded and extracted the files, and ran ./configure on that.  Here's what I got:

3) Not sure what anything above means, whether it worked or not, so I moved on and ran "make".  I got the following:


I pretty much left it there....didn't seem like it worked and I have NO idea how to get it work. I'm not even sure what the commands are that I did do....I was just following the Install text.  Like I said, any help for this lost noob would be much appreciated.

Thanks a lot.
i know its in the repos, but its part of the linux learning process. so....
in the libao folder, run ```
sudo make install
```

---

### Post by djm227 on 2009-11-18
Well I feel pretty stupid.  I looked in the software center and since it wasn't there I figured I'd have to do it the hard way.  Thanks for the help.

---

### Post by Cheesemill on 2009-11-18
> **QIII said:**
> Aw, cheesemill -- give an old fart a break!

Fingers aren't so fast, bifocals make it hard to see the keyboard...

Don't worry mate, it's happened twice to me today (one of them was even ***identical***) !!

---

### Post by QIII on 2009-11-18
There are no stupid people here.

There is only a continuum of people who have much to learn to people who have learned much.

We all have more to learn.

---

### Post by Cheesemill on 2009-11-18
> **djm227 said:**
> Well I feel pretty stupid.  I looked in the software center and since it wasn't there I figured I'd have to do it the hard way.  Thanks for the help.

I found it using:
```
apitude search aldo
```

It's a useful command to remember.

---

### Post by djm227 on 2009-11-18
Is there room for one more newbie question in this thread?

I installed in in terminal, but it is not in any application menu. I tried using gnome-do and application finder to find it, but no go.  Terminal confirms that Aldo was installed.  What am I doing wrong?  Unless it's a terminal based program and not a GUI.....

---

### Post by Cheesemill on 2009-11-18
It's a terminal only program, either open a terminal and type
```
aldo
```
or hit ALT + F2, type aldo, and check the 'Run in terminal' box.

---

### Post by WatchHerDie on 2009-11-18
Check to make sure there are no lines to be added to your sources list.
Google "How to install Aldo" or something along those lines and you should be able to tell.

Here is how you can access the Gnome terminal fast: ALT+F2, then type in "gnome-terminal" and press enter/return

Now type this in if there are sources to be added:
```
sudo nano /etc/apt/sources.list
```After you have added your line(s), then press CTRL+X, followed by Y, and then enter/return.

Hope this helps you somehow.

---

### Post by Cheesemill on 2009-11-18
> **WatchHerDie said:**
> Check to make sure there are no lines to be added to your sources list.
Google "How to install Aldo" or something along those lines and you should be able to tell.

Here is how you can access the Gnome terminal fast: ALT+F2, then type in "gnome-terminal" and press enter/return

Now type this in if there are sources to be added:
```
sudo nano /etc/apt/sources.list
```After you have added your line(s), then press CTRL+X, followed by Y, and then enter/return.

Hope this helps you somehow.
The OP already has it installed, they just needed to know how to run it.

djm227 - If you want a menu entry for it, do the following:


[LIST]
[*]Right-click on Applications and select 'Edit Menus'
[*]Select a sub-menu then click 'New Item'
[*]Change 'Application' to 'Application in Terminal'
[*]Enter 'ALDO' as the name and 'aldo' as the command
[*]Hit OK and you're all done
[/LIST]

---

### Post by djm227 on 2009-11-19
> **Cheesemill said:**
> The OP already has it installed, they just needed to know how to run it.

djm227 - If you want a menu entry for it, do the following:


[LIST]
[*]Right-click on Applications and select 'Edit Menus'
[*]Select a sub-menu then click 'New Item'
[*]Change 'Application' to 'Application in Terminal'
[*]Enter 'ALDO' as the name and 'aldo' as the command
[*]Hit OK and you're all done
[/LIST]



Worked great,  thank you

---

