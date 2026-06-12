---
title: "[SOLVED] Make error..."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by *Lyg%$#hj on 2008-12-07
I'm trying to install a program called Accountability Pal (a URL tracker) on my Ubuntu and have successfully configured it, but when I try the 'make' command, I get the following error:

zak@zak-ubuntu:~/accpal$ make
make  all-recursive
make[1]: Entering directory `/home/zak/accpal'
Making all in src
make[2]: Entering directory `/home/zak/accpal/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2   -o accpal  accpal.o common.o -ldl -lpcap 
gcc -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -g -O2 -o accpal accpal.o common.o  -ldl -lpcap
/usr/local/lib/libpcap.a(gencode.o): In function `.L149':
gencode.c:(.text+0x7b4): undefined reference to `pcap_parse'
collect2: ld returned 1 exit status
make[2]: *** [accpal] Error 1
make[2]: Leaving directory `/home/zak/accpal/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zak/accpal'
make: *** [all] Error 2


I am running Ubuntu 8.10 on a Macbook 4,1 and very recently installed it.
Any help would be appreciated,


seatdistrict

---

### Post by Denestria on 2008-12-07
Do you have the development package for libpcap installed?

---

### Post by *Lyg%$#hj on 2008-12-07
Yes, that was the initial problem I had, but I fixed it by getting flex and bison in order to get libpcap.  Before I installed libpcap, I was unable to compile accpal.  Now I am just having trouble with 'make' ('make install' didn't work either)

Thanks

---

### Post by andrew.46 on 2008-12-07
Hi,

There is a requirement for:

> INSTALLATION FROM SOURCE CODE ON LINUX/UNIX
-------------------------------------------

Prior to installing, you will need the following installed:

- libharu PDF library
	[http://sourceforge.net/projects/libharu/](http://sourceforge.net/projects/libharu/)

Do you have this one?

  Andrew

---

### Post by *Lyg%$#hj on 2008-12-08
No, I didn't have that one.  I have just downloaded it, and I configured, but I received another error message after I tried 'make.'  The installation instructions say to configure, then run 'make clean' (which worked), then 'make,' and then 'make install.'  Neither of the last two works.

This is the error I received when attempting to 'make' libharu:

zak@zak-ubuntu:~/libharu-2.0.8$ make
gcc -o src/hpdf_utils.o -Iinclude -O2 -Wall  -c src/hpdf_utils.c
src/hpdf_utils.c: In function ‘HPDF_StrCpy’:
src/hpdf_utils.c:269: warning: pointer targets in return differ in signedness
src/hpdf_utils.c: In function ‘HPDF_StrStr’:
src/hpdf_utils.c:373: warning: pointer targets in passing argument 1 of ‘HPDF_MemCmp’ differ in signedness
src/hpdf_utils.c:373: warning: pointer targets in passing argument 2 of ‘HPDF_MemCmp’ differ in signedness
gcc -o src/hpdf_error.o -Iinclude -O2 -Wall  -c src/hpdf_error.c
gcc -o src/hpdf_mmgr.o -Iinclude -O2 -Wall  -c src/hpdf_mmgr.c
gcc -o src/hpdf_list.o -Iinclude -O2 -Wall  -c src/hpdf_list.c
gcc -o src/hpdf_streams.o -Iinclude -O2 -Wall  -c src/hpdf_streams.c
src/hpdf_streams.c:20:18: error: zlib.h: No such file or directory
src/hpdf_streams.c:21:19: error: zconf.h: No such file or directory
src/hpdf_streams.c: In function ‘HPDF_Stream_ReadLn’:
src/hpdf_streams.c:163: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Read’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteChar’:
src/hpdf_streams.c:253: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteStr’:
src/hpdf_streams.c:263: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteInt’:
src/hpdf_streams.c:281: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteReal’:
src/hpdf_streams.c:299: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteEscapeName’:
src/hpdf_streams.c:407: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteEscapeText2’:
src/hpdf_streams.c:447: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c:455: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteBinary’:
src/hpdf_streams.c:521: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c:532: warning: pointer targets in passing argument 2 of ‘HPDF_Stream_Write’ differ in signedness
src/hpdf_streams.c: In function ‘HPDF_Stream_WriteToStreamWithDeflate’:
src/hpdf_streams.c:554: error: ‘z_stream’ undeclared (first use in this function)
src/hpdf_streams.c:554: error: (Each undeclared identifier is reported only once
src/hpdf_streams.c:554: error: for each function it appears in.)
src/hpdf_streams.c:554: error: expected ‘;’ before ‘strm’
src/hpdf_streams.c:555: error: ‘Bytef’ undeclared (first use in this function)
src/hpdf_streams.c:555: error: expected ‘;’ before ‘inbuf’
src/hpdf_streams.c:556: error: expected ‘;’ before ‘otbuf’
src/hpdf_streams.c:567: error: ‘strm’ undeclared (first use in this function)
src/hpdf_streams.c:568: error: ‘otbuf’ undeclared (first use in this function)
src/hpdf_streams.c:571: warning: implicit declaration of function ‘deflateInit_’
src/hpdf_streams.c:571: error: ‘Z_DEFAULT_COMPRESSION’ undeclared (first use in this function)
src/hpdf_streams.c:571: error: ‘ZLIB_VERSION’ undeclared (first use in this function)
src/hpdf_streams.c:573: error: ‘Z_OK’ undeclared (first use in this function)
src/hpdf_streams.c:576: error: ‘inbuf’ undeclared (first use in this function)
src/hpdf_streams.c:594: warning: implicit declaration of function ‘deflateEnd’
src/hpdf_streams.c:600: warning: implicit declaration of function ‘deflate’
src/hpdf_streams.c:600: error: ‘Z_NO_FLUSH’ undeclared (first use in this function)
src/hpdf_streams.c:601: error: ‘Z_STREAM_END’ undeclared (first use in this function)
src/hpdf_streams.c:629: error: ‘Z_FINISH’ undeclared (first use in this function)
make: *** [src/hpdf_streams.o] Error 1


Thanks,

---

### Post by andrew.46 on 2008-12-08
Hi,

I hope you are *really* after this program :-). I note the rot starts with a reference to zlib in your compiling effort. From the haru docs:
> 
Also on platforms except the above, it is easy to build HARU. If you success to build HARU on other platforms, please send makefile to me.
**[COLOR="Red"]In addition, ZLIB and PNGLIB are required when you want to use the features of compression and embedding PNG images. (In[/COLOR]** the case of Windows, static library files for several compilers are included in the package for WIndows.  In the case of  most of UNIX, these libraries are usually installed.)

Now you have caught me on the wrong partition so I cannot access the Ubuntu repositories but you need 'dev' files for zlib and pnglib | png. The easiest way to find the files is the query the repository as follows:

```
$ apt-cache search zlib | grep dev
$ apt-cache search pnglib | grep dev
```

and this should show you the correct files to download.

All the best,

  Andrew

---

### Post by xjcannonx on 2008-12-08
If you cant get this to work, there is another tracker out there called 'net-responsibility'

By the way, are you using 64bit, don't know for sure but that may have something to do with it

---

### Post by mbsullivan on 2008-12-08
> By the way, are you using 64bit, don't know for sure but that may have something to do with it 

Just FYI, if you don't know how to tell if you're using a 64-bit or 32-bit version of Ubuntu, do the following:

```
uname -ar
```

And look @ the end of the printout. If it says "i686", you have 32-bit Linux installed. If it says "x86_64", you have 64-bit.

Mike

---

### Post by *Lyg%$#hj on 2008-12-08
I am running 32 bit Ubuntu.  
Andrew - I tried the commands that you recommended above, and the first one (zlib) gave me an output that I can't interpret very well.  The second one (pnglib) gave no output.  This is the output for both:

zak@zak-ubuntu:~$ apt-cache search zlib | grep dev
lib64z1-dev - compression library - 64 bit development
libmng-dev - M-N-G library (Development headers)
zlib1g-dbg - compression library - development
zlib1g-dev - compression library - development
libcryptokit-ocaml-dev - cryptographic algorithm library for OCaml - development
libnifti1-dev - IO libraries for the NIfTI-1 data format
libpnglite-dev - lightweight C library for loading and writing PNG images
libtrf-tcl-dev - Tcl data transformations - development files
libtrf-tcl-doc - Tcl data transformations - development files
libzlcore-dev - ZLibrary core - development files
libzltext-dev - ZLibrary text model/viewer - development files
libzzip-dev - library providing read access on ZIP-archives - development
zak@zak-ubuntu:~$ apt-cache search pnglib | grep dev
zak@zak-ubuntu:~$

Please let me know if there is a way to fix this, in the meantime, I will try the other program recommended by xjcannonx.

Thanks,

---

### Post by mc4man on 2008-12-08
> zlib1g-dev 
for png stick the lib in front as in libpng ( most likely libpng12-dev

---

### Post by *Lyg%$#hj on 2008-12-08
OK, I performed the searches for zlib and libpng and downloaded most of the files with apt-get install, yet I am still encountering an error when I try 'make' for accpal:

zak@zak-ubuntu:~/accpal$ make
make  all-recursive
make[1]: Entering directory `/home/zak/accpal'
Making all in src
make[2]: Entering directory `/home/zak/accpal/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2   -o accpal  accpal.o common.o -ldl -lpcap 
gcc -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -g -O2 -o accpal accpal.o common.o  -ldl -lpcap
/usr/local/lib/libpcap.a(gencode.o): In function `.L149':
gencode.c:(.text+0x7b4): undefined reference to `pcap_parse'
collect2: ld returned 1 exit status
make[2]: *** [accpal] Error 1
make[2]: Leaving directory `/home/zak/accpal/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zak/accpal'
make: *** [all] Error 2
zak@zak-ubuntu:~/accpal$ 


Thanks for your patience,

---

### Post by mc4man on 2008-12-08
Can you post a link to the source your using for accpal?

Just to backtrack, did you install libharu (libhdpf) as suggested and if so what was your configure on it?

---

### Post by *Lyg%$#hj on 2008-12-08
Here is the link for the source:

[http://sourceforge.net/project/showfiles.php?group_id=126818](http://sourceforge.net/project/showfiles.php?group_id=126818)

I was directed there from the download link on the app's page:

[http://www.accountabilitypal.org/](http://www.accountabilitypal.org/)

--
I attempted to install libharu, but encountered an error when I tried to run 'make.'  Then I installed the zlib and libpng packages that came up after 'apt-cache search.'
I just now tried to make libharu again, this time successfully, but I still can't make accpal.

When you ask for the "configure on it," do you want the output of ./configure, or the content of the 'configure' file in the source directory, or something else?

Thanks,

---

### Post by mc4man on 2008-12-08
Took me a bit to figure out (I think). 
It appears you need to use Version 1.2.4 of libharu. The 2.0.8 creates a hdpf.h but your accpal is looking for libharu.h

Give me awhile to backtrack, though it did make successfully - 
> doug@doug-desktop:~/Desktop/accpal-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a BSD-compatible install... /usr/bin/install -c
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking net/ethernet.h usability... yes
checking net/ethernet.h presence... yes
checking for net/ethernet.h... yes
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for gethostbyaddr... yes
checking for inet_ntoa... yes
checking for memset... yes
checking for strchr... yes
checking for strstr... yes
checking for an ANSI C-conforming const... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether closedir returns void... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for strftime... yes
checking for dirent.h that defines DIR... (cached) yes
checking for library containing opendir... (cached) none required
checking for ranlib... (cached) ranlib
checking whether struct tm is in sys/time.h or time.h... time.h
checking return type of signal handlers... void
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating plugins/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
doug@doug-desktop:~/Desktop/accpal-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/doug/Desktop/accpal-0.1.1'
Making all in src
make[2]: Entering directory `/home/doug/Desktop/accpal-0.1.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2 -MT accpal.o -MD -MP -MF ".deps/accpal.Tpo" -c -o accpal.o accpal.c; \
	then mv -f ".deps/accpal.Tpo" ".deps/accpal.Po"; else rm -f ".deps/accpal.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2 -MT common.o -MD -MP -MF ".deps/common.Tpo" -c -o common.o common.c; \
	then mv -f ".deps/common.Tpo" ".deps/common.Po"; else rm -f ".deps/common.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2   -o accpal  accpal.o common.o -ldl -lpcap 
mkdir .libs
gcc -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -g -O2 -o accpal accpal.o common.o  -ldl -lpcap
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2 -MT apreport.o -MD -MP -MF ".deps/apreport.Tpo" -c -o apreport.o apreport.c; \
	then mv -f ".deps/apreport.Tpo" ".deps/apreport.Po"; else rm -f ".deps/apreport.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" [COLOR="Red"]-DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2   -o apreport  apreport.o common.o -ldl -lpcap -lharu -lstdc++ -lz [/COLOR]
gcc -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -g -O2 -o apreport apreport.o common.o  -ldl -lpcap -lharu -lstdc++ -lz
make[2]: Leaving directory `/home/doug/Desktop/accpal-0.1.1/src'
Making all in plugins
make[2]: Entering directory `/home/doug/Desktop/accpal-0.1.1/plugins'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2 -MT http.lo -MD -MP -MF ".deps/http.Tpo" -c -o http.lo http.c; \
	then mv -f ".deps/http.Tpo" ".deps/http.Plo"; else rm -f ".deps/http.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT http.lo -MD -MP -MF .deps/http.Tpo -c http.c  -fPIC -DPIC -o .libs/http.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT http.lo -MD -MP -MF .deps/http.Tpo -c http.c -o http.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2 -MT redblack.lo -MD -MP -MF ".deps/redblack.Tpo" -c -o redblack.lo redblack.c; \
	then mv -f ".deps/redblack.Tpo" ".deps/redblack.Plo"; else rm -f ".deps/redblack.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT redblack.lo -MD -MP -MF .deps/redblack.Tpo -c redblack.c  -fPIC -DPIC -o .libs/redblack.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT redblack.lo -MD -MP -MF .deps/redblack.Tpo -c redblack.c -o redblack.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2 -MT common.lo -MD -MP -MF ".deps/common.Tpo" -c -o common.lo `test -f '../src/common.c' || echo './'`../src/common.c; \
	then mv -f ".deps/common.Tpo" ".deps/common.Plo"; else rm -f ".deps/common.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT common.lo -MD -MP -MF .deps/common.Tpo -c ../src/common.c  -fPIC -DPIC -o .libs/common.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT common.lo -MD -MP -MF .deps/common.Tpo -c ../src/common.c -o common.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2   -o libhttp.la -rpath /usr/local/lib/accpal -no-undefined http.lo redblack.lo common.lo  
gcc -shared  .libs/http.o .libs/redblack.o .libs/common.o   -Wl,-soname -Wl,libhttp.so.0 -o .libs/libhttp.so.0.0.0
(cd .libs && rm -f libhttp.so.0 && ln -s libhttp.so.0.0.0 libhttp.so.0)
(cd .libs && rm -f libhttp.so && ln -s libhttp.so.0.0.0 libhttp.so)
ar cru .libs/libhttp.a  http.o redblack.o common.o
ranlib .libs/libhttp.a
creating libhttp.la
(cd .libs && rm -f libhttp.la && ln -s ../libhttp.la libhttp.la)
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..     -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2 -MT p2p.lo -MD -MP -MF ".deps/p2p.Tpo" -c -o p2p.lo p2p.c; \
	then mv -f ".deps/p2p.Tpo" ".deps/p2p.Plo"; else rm -f ".deps/p2p.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT p2p.lo -MD -MP -MF .deps/p2p.Tpo -c p2p.c  -fPIC -DPIC -o .libs/p2p.o

 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -I../src -g -O2 -MT p2p.lo -MD -MP -MF .deps/p2p.Tpo -c p2p.c -o p2p.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -I../src -g -O2   -o libp2p.la -rpath /usr/local/lib/accpal -no-undefined p2p.lo redblack.lo common.lo  
gcc -shared  .libs/p2p.o .libs/redblack.o .libs/common.o   -Wl,-soname -Wl,libp2p.so.0 -o .libs/libp2p.so.0.0.0
(cd .libs && rm -f libp2p.so.0 && ln -s libp2p.so.0.0.0 libp2p.so.0)
(cd .libs && rm -f libp2p.so && ln -s libp2p.so.0.0.0 libp2p.so)
ar cru .libs/libp2p.a  p2p.o redblack.o common.o
ranlib .libs/libp2p.a
creating libp2p.la
(cd .libs && rm -f libp2p.la && ln -s ../libp2p.la libp2p.la)
make[2]: Leaving directory `/home/doug/Desktop/accpal-0.1.1/plugins'
make[2]: Entering directory `/home/doug/Desktop/accpal-0.1.1'
make[2]: Leaving directory `/home/doug/Desktop/accpal-0.1.1'
make[1]: Leaving directory `/home/doug/Desktop/accpal-0.1.1'
doug@doug-desktop:~/Desktop/accpal-0.1.1$ 


---

### Post by mc4man on 2008-12-08
I think you'd need to decide if you want to install accpal to /usr or /usr/local. (I don't know there

It doesn't seem to matter where you install libharu. So to install that
cd to the extracted haru folder and run

```
sudo make -f makefile.gcc install
```

This will install to /usr/local/lib
If you wanted (?) to install to /usr/lib then you need to modify the makefile (makefile.gcc) before running above. ( or any other changes

Make sure you installed libpng12-dev  (use synaptic

---

### Post by *Lyg%$#hj on 2008-12-08
OK, I ran the command:  sudo  make -f makefile.gcc install, but I had already run the same command without the 'install' at the end, according to the README.  I don't know if that changes anything.

My usr/local/lib/ directory now contains:

zak@zak-ubuntu:/usr/local/lib$ ls
libharu.a         libhpdf.a   libhpdf.so  python2.5
libhpdf-2.1.0.so  libhpdf.la  libpcap.a   site_ruby

---

### Post by mc4man on 2008-12-08
Are you still failing at the same spot?

I marked in previous post in red where the later version of 'haru'  had caused the make to fail.

Are you making it that far?

the libharu.a is what you'd want to see

---

### Post by *Lyg%$#hj on 2008-12-08
I think it is still failing in the same spot, I definitely don't reach what you highlighted.  Here's the output:

zak@zak-ubuntu:~/accpal$ make
make  all-recursive
make[1]: Entering directory `/home/zak/accpal'
Making all in src
make[2]: Entering directory `/home/zak/accpal/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -DSYSCONFDIR="\"/usr/local/etc\"" -DPKGLIBDIR="\"/usr/local/lib/accpal\"" -DLOGDIR="\"/usr/local/var/log/accpal\"" -g -O2   -o accpal  accpal.o common.o -ldl -lpcap 
gcc -DSYSCONFDIR=\"/usr/local/etc\" -DPKGLIBDIR=\"/usr/local/lib/accpal\" -DLOGDIR=\"/usr/local/var/log/accpal\" -g -O2 -o accpal accpal.o common.o  -ldl -lpcap
/usr/local/lib/libpcap.a(gencode.o): In function `.L149':
gencode.c:(.text+0x7b4): undefined reference to `pcap_parse'
collect2: ld returned 1 exit status
make[2]: *** [accpal] Error 1
make[2]: Leaving directory `/home/zak/accpal/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zak/accpal'
make: *** [all] Error 2
zak@zak-ubuntu:~/accpal$

It looks like there is a problem here, but I'm not sure what it is:
gencode.c:(.text+0x7b4): undefined reference to `pcap_parse'

---

### Post by mc4man on 2008-12-08
I'm an idiot for not going back to beginning of thread, your using 8.10 and I'm on 8.04 atm. Sorry about that.

I'll give it a go on 8.10, will take a few to set up for compiling.

As a longshot try installing this (no reason it should help, but i remember when using 8.10 beta it somehow did
ccache

---

### Post by mc4man on 2008-12-08
2 things

Built fine on 8.10

On 8.04 I made a couple of .debs (one installs to /usr, the other to /usr/local.
I didn't install the make on 8.10, instead I installed the .deb from 8.04, which installed fine.

How you use this I'm clueless though it seems to be workable;
> doug@doug-desktop:~$ sudo accpal
[sudo] password for doug: 
Accountability Pal 0.1.1
Copyright (C) 2004-2005 Brian C. Wiles.  All Rights Reserved.

Could not open ethernet device "\Device\NPF_{ABCDCB01-123A-9123-8158-43DFF14786BB}".  Available devices are:
1. eth0
	Address Family Name: Unknown
	IP Address: 192.168.1.107/255.255.255.0
	Address Family Name: Unknown

2. any
	Pseudo-device that captures on all interfaces

3. lo
	Address Family Name: Unknown
	IP Address: 127.0.0.1/255.0.0.0
	Address Family Name: Unknown


In accpal.conf, set "Interface" to one of these devices.

Press <ENTER> to continue...


If you can't resolve and want to try I'll upload a .deb to mediafire, just sayso (and which one


Edit : here's my package list on a new 8.10 install for this build (go thru and ck. in synaptic

> 
build-essential (11.4)
ccache (2.4-15)
dpkg-dev (1.14.20ubuntu6)
g++ (4:4.3.1-1ubuntu2)
g++-4.3 (4.3.2-1ubuntu11)
libpcap-dev (0.9.8-5)
libpcap0.8-dev (0.9.8-5)
libpng12-dev (1.2.27-1)
libstdc++6-4.3-dev (4.3.2-1ubuntu11)
zlib1g-dev (1:1.2.3.3.dfsg-12ubuntu1)
cpp-4.2 (4.2.4-3ubuntu4)
gcc-4.2 (4.2.4-3ubuntu4)
gcc-4.2-base (4.2.4-3ubuntu4)
libjpeg62-dev (6b-14)

---

### Post by *Lyg%$#hj on 2008-12-08
I checked and installed all of those packages and retried 'make,' which worked to my great surprise.  It is now installed, supposedly, and I will test it out.

You've really gone to great lengths to help me with this, I really appreciate it.

Thanks,

---

### Post by mc4man on 2008-12-08
if you ever figure out how to configure it I'd be curious.
I gather running - 
accpal -starts
apreport - gives report
sudo accpal - shows avail. interfaces
sudo gedit /usr/local/etc/accpal.conf or /usr/etc/accpal.conf is where the conf is.

Couldn't see how to add/edit to the interface line ( I'm kinda stupid that way
anyway -  good luck


Edit" 
possibly too late to mention
if you want to uninstall you'll need your source/build folder so don't delete it. CDing to the source/build folder and running
```
sudo make uninstall 
```will do the trick.

If you find it useful but want to to delete the source folder than install 'checkinstall'

You can build a .deb *with it installed* by simply cding to your build folder and going 
```
sudo checkinstall --install=no
```

Then run the make uninstall, and use your.deb to reinstall

Due to some bug in checkinstall it will not build a deb if this app isn't installed, hence the install=no.

I believe there is a checkinstall command to get around this but it escapes me ATM.

---

### Post by andrew.46 on 2008-12-09
Hi seatdistrict,

Good to see you got it all installed! I suspect I would have given up a while ago :-).

  Andrew

---

### Post by xtemplarx on 2010-04-28
Once installed, has anybody gotten it configured and working?  I've set up the configuration, even getting some tips/information from the author of the software.  However, once run, the app doesn't appear to be doing anything as of yet.

---

### Post by kevorski on 2010-07-23
[http://www.netresponsibility.com](http://www.netresponsibility.com)

Try this!

---

### Post by greenwom on 2010-09-19
netresponibility is not working as well.  the automatic sending of the reports is broken, so whats the point...

I tried to run the report manually with it and nothing was sent. 
So no point in setting up a cron job...

with accountability pal I'm stuck in the same failure to "make" the package.
i'm getting the libharuc.h error and have not been able to install the older version of haru

---

### Post by jbhoward on 2011-08-23
> **seatdistrict said:**
> I checked and installed all of those packages and retried 'make,' which worked to my great surprise.  It is now installed, supposedly, and I will test it out.

You've really gone to great lengths to help me with this, I really appreciate it.

Thanks,

Hello, my son just installed Zorin Core 5 on his laptop... his (and my) first foray into Linux. I've read through this thread but must admit most of it is way over my head.

He would like to get accountability software installed on his machine, and it looks like you succeeded with this. Do you have an "Idiot's Guide" version of the steps you took to get this installed?

We would both appreciate it very much! Thanks!

Blessings,
Jim Bob

---

### Post by *Lyg%$#hj on 2011-08-23
> **jbhoward said:**
> Hello, my son just installed Zorin Core 5 on his laptop... his (and my) first foray into Linux. I've read through this thread but must admit most of it is way over my head.

He would like to get accountability software installed on his machine, and it looks like you succeeded with this. Do you have an "Idiot's Guide" version of the steps you took to get this installed?



Unfortunately, after getting it installed, I was never able to get it working, and gave up. Honestly, I'm not aware of any working accountability setup for linux, though I haven't looked since trying this one. 

The way linux operates makes it very difficult for accountability software, such as Covenant Eyes, to function, because linux emphasises the need for the user to be in control and aware of as much as possible running on the system. Without depriving your son of administrator privileges (and therefore the opportunity to learn anything about linux, or use it to do basically anything he would want/need to do with it) and writing your own complex script to email yourself a URL log, I'm not sure what you could do.

Sorry I don't have a better answer for you, good luck to you and your son with linux.

---

