---
title: "Help! GTK + 2.8 required?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-08
Hi,
I'm trying to install this:
[http://www.cimitan.com/murrine/project/murrine](http://www.cimitan.com/murrine/project/murrine)

When I do ./configure, it does it's thing, but won't allow me to compile.

I am returned with the error:
configure: error: GTK+-2.8 is required to compile murrine

How do I install/update GTK +?

---

### Post by taurus on 2009-03-08
Are you talking about gtk+2-engine-murrine (& murrine-themes)?  They are both in the repos.

---

### Post by m4lte on 2009-03-08
Go to System > Administration > Synaptic Package Manager, and search for 'libgtk2.0-0' (package description: The GTK+ graphical user interface library). Installing that item should install the most recent version 2.14

Also try installing the packages mentioned in the previous reply, using the same method.

---

### Post by Gp. on 2009-03-08
> **taurus said:**
> Are you talking about gtk+2-engine-murrine (& murrine-themes)?  They are both in the repos.

repos?

And I already have libgtk2.0-0 installed.

:S

---

### Post by taurus on 2009-03-08
If you need to install something, do a **Search** in System -> Administration -> Synaptic Package Manager first.

---

### Post by Gp. on 2009-03-08
I did.
The libraries are already installed.
Still gives me the same error.

"checking for GTK... no
configure: error: GTK+-2.8 is required to compile murrine"


OR the full messages are

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: GTK+-2.8 is required to compile murrine

---

### Post by snova on 2009-03-08
Try installing **libgtk2.0-dev**.

---

### Post by Gp. on 2009-03-09
This worked.

Also, what does it mean when it compiles a package? what's that for, whats it actually doing?

---

### Post by cariboo on 2009-03-09
> **Gp. said:**
> This worked.

Also, what does it mean when it compiles a package? what's that for, whats it actually doing?

Have a look at this [page]("http://purple.niagara.edu/boxer/essays/prog/compiling.htm") for an explanation as to what compiling does.

Jim

---

