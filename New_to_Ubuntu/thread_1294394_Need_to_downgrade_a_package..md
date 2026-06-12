---
title: "Need to downgrade a package."
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-10-18
Hi there.

I have recently installed a program called KDevelop, but after having some issues with it, I've discovered I need to downgrade a package called 'libtool' in order for it to work.

I was hoping someone could provide me the commands used to do that. 

Never done it before, and I badly don't want to mess up my installation.

Apparently I need to downgrade from libtool 2.2.4 to 1.5.X.X.

Thanks for any help with this, it's really appreciated!

---

### Post by yeats on 2009-10-18
You'll want to be very careful changing library programs - that is a great way to bork your system (speaking from experience).

I see that kdevelop is in the repositories - that version would only rely on current versions of dependencies... Did you install this from source?

---

### Post by Swerve1000 on 2009-10-18
Thanks chrissharp123,

I used *sudo apt-get install kdevelop* to install it. But after doing so I've found lots of people have the exact same issue, but no explanation on how to downgrade.

I hope that answers whether I installed from source.

---

### Post by sisco311 on 2009-10-18
try:
```
sudo apt-get install libtool=1.5.26-1ubuntu1
```

or in Synaptic search for libtool, highlight the package and select *Force Version...* from the *Package* menu.

---

### Post by Swerve1000 on 2009-10-18
Hi sisco, thanks for that.

It appeared that that version wqasn't avaialable in the repository,so I downloaded the .tar.gz version and installed that.

Every seemed to go OK, but now when I create a new project in KDevelop (Hello World in C++) I get the following output:

> 
Vcd '/home/me/HW' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/a/HW/debug' && cd '/home/a/HW/debug' && CXXFLAGS="-O0 -g3" "/home/a/HW/configure" --enable-debug=full && cd '/home/a/HW/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k
aclocal
autoheader
automake
autoconf
configure: WARNING: unrecognized options: --enable-debug
installing -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
linking file.o... (gcc)
linking file.o... (gcc)
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
linking file.o... (g++)
linking file.o... (g++)
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
configure: WARNING: unrecognized options: --enable-debug
make all-recursive
Making all in src
compiling hw.cpp (g++)
mv -f .deps/hw.Tpo .deps/hw.Po
linking hw (g++)
../libtool: line 835: X--tag=CXX: command not found
../libtool: line 868: libtool: ignoring unknown tag : command not found
../libtool: line 835: X--mode=link: command not found
../libtool: line 1002: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 1003: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
gcc: no input files
gcc: no input files
gcc: no input files
gcc: no input files
../libtool: line 2240: X-O0: command not found
../libtool: line 2240: X-g3: command not found
make[2]: Nothing to be done for `all-am'.
../libtool: line 2409: Xhw: command not found
X: user not authorized to run the X server, aborting.
../libtool: line 2421: Xhw: command not found
../libtool: line 2429: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make[2]: *** [hw] Error 1
make[2]: Target `all' not remade because of errors.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 *** 

Which totally has me confused. 

It certainly seems to progress further than it did before, but still fails to compile.

If anyone has any ideas, they are most welcome as I need to get this working as soon as possible.

Thanks :)

---

