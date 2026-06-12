---
title: "Installing or Compiling a program from a tar or Source File"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Dorotheos on 2009-03-31
Okay everyone, i have read several discussions on how to do this, however no one has discussed the most important aspect of this! That is how to find the missing dependencies!

So i have three programs i am trying to make:
fung-calc-1.3.2b
Jahshaka
Jahplayer
and some other ones too!

I have come to realize that this is a very important skill yet can't understand how to accomplish this.

So here goes.

I saved the tar with the source to my desktop

i open a terminal and type tar -xzvf [filename]

it then extracts the folder to my desktop

i cd into the [filename]

i run ./comfigure

this is what i read:

-------------------------------------------------------------------------

******@****:~/Desktop/fung-calc-1.3.2b$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -frepo... yes
not using lib directory suffix
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... 
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... no
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for char... yes
checking size of char... 1
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
******@***:~/Desktop/fung-calc-1.3.2b$
-----------------------------------------------------

Ok so my first question is, what does that mean?

Second question, i assumed that it had to do with missing dependencies so i tried to download build-essentials. But honestly i don't know how to use that! 
so while in the folder i run:
--------------------------------------------------------------------------


*****@*****:~/Desktop/fung-calc-1.3.2b$ sudo apt-get build-dep
[sudo] password for dorotheos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Must specify at least one package to check builddeps for
******@****:~/Desktop/fung-calc-1.3.2b$ 
----------------------

I think the problem is that i didn't specifiy a program

so i try that:

--------------------
****@****:~/Desktop/fung-calc-1.3.2b$ sudo apt-get build-dep fung-calc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for fung-calc
*****@****:~/Desktop/fung-calc-1.3.2b$

--------------

Now when i read this i figure it's telling me it can't find the file in the repositories, but that;s why i have to compile it from source in the first place!

Someone please help!

---

### Post by 3rdalbum on 2009-04-01
The bit about "sudo apt-get build-dep x" is for if you want to compile the latest version of a program that has an older version in the repositories. So, in your case, it won't work. If you wanted the latest version of Banshee, for instance, you'd type "sudo apt-get build-dep banshee" and it would get the build dependencies. It would actually get the build dependencies for the version of Banshee that is already in the repositories, but most of the time that's enough.

So, the configure script says that it can't find X - that is, the Xorg display server. You already have the display server, but when you are compiling you need the "development libraries"; basically, all the *related* packages with -dev at the end of the package name.

The best candidate for this particular dependency appears to be "xserver-xorg-dev". This will probably install about 50 megabytes worth of packages, from memory.

After that's all installed, just run the ./configure script again and it'll probably complain about a different missing library. Remember, we're looking for packages with "-dev" at the end. Usually typing some of the library's name into Synaptic's Find box will help you.

---

### Post by ibuclaw on 2009-04-01
My initial guess would be
```
sudo apt-get install build-essential x-dev
```

If you continue to get errors, type in
```
ls
```
With most projects there is usually a dependency list in a file named **README** or **INSTALL**.

I suggest you take a look inside them before continuing.

Regards
Iain

---

### Post by zvacet on 2009-04-01
For compiling **fung-calc-1.3.2b** you need Qt.I found that info [here.]("http://sourceforge.net/forum/forum.php?thread_id=1041373&forum_id=213285")You need build-essential to make deb package.It will be used during compiling.For other packages on your list first run 

```
sudo apt-get build-dep package_name
```

---

### Post by Dorotheos on 2009-04-21
Hey thanks guys! this is all really helpful! Im looking for the dependancies now!

---

