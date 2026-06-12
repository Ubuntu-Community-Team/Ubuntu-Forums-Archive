---
title: "Hard time using the &quot;make&quot; command?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by Livin4Jesus on 2011-08-23
Apparently, for almost everyone else, building a program is as easy as 123. But not for me...
Whenever I attempt to build a program, there's always an error that prevents me from building! I have the latest version of make, I always read the INSTALL instructions, etc., but it still just will not build! Anyone know why?

---

### Post by papibe on 2011-08-23
Difficult to say without more information.

What are you trying to compile?
Where did you get the code?
Could you post the error messages you are getting?

Regards.

---

### Post by Rex Bouwense on 2011-08-23
While many of the people on this forum are super when it comes to solving problems, even they are going to need some more information.  We have no idea what the specific problem is.  If you want a solution, then details are your friend.

---

### Post by Livin4Jesus on 2011-08-23
ATM, I'm trying to compile ZSNES 1.51. When I type in "make" in the src directory, I get this error...

```
livin4jesus@livin4jesus-desktop:~/Downloads/zsnes_1_51/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -s -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function ‘static int ci_char_traits::compare(const char*, const char*, size_t)’:
tools/strutil.h:34: error: ‘strncasecmp’ was not declared in this scope
make: *** [tools/strutil.o] Error 1
```

Anyone know why this is happening?

---

### Post by papibe on 2011-08-23
Which version of Ubuntu are using?
Is it 32bits or 64bits?

Regards.

---

### Post by anewguy on 2011-08-23
What specifically did the readme or install text say to do?  The normal procedure is to:

- unpack the file you downloaded.  This usually creates a subfolder that usually has the name in it somewhere - for example, if you downloaded "mystuff", then unpacked it, it usually creates a folder with "mystuff" in the name

- cd to the newly created folder - in the example above "mystuff"

- configure (it's probably something like ./configure)

- make

- sudo make install

There are also some prerequisite packages to install - build-essential is the main package you must have installed.  Others vary.

So, please post back what the install or readme text tells you to do.

Dave ;)

---

### Post by papibe on 2011-08-23
Another question: Did the version on the repos didn't work for you? As far as I can see it is up to date.

Regards.

---

### Post by Paqman on 2011-08-23
> **Livin4Jesus said:**
> ATM, I'm trying to compile ZSNES 1.51.

Is there some reason you're trying to compile this? The version available in the Software Centre is 1.51.

Generally speaking, compiling programs from source should be avoided at all costs. The Ubuntu repositories are always the first place you should look to get software. That way it'll install and uninstall easily and updates will come through automatically. I haven't compiled anything from source in years.

---

### Post by sbraz on 2011-08-23
./autogen.sh

then, you have to figure out what's missing, step by step, like this:
```
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **ls**
acinclude.m4  chips         configure.in  effects     icons       jma             makefile.ms  objfix.c      ui.c        zip        zpath.c
argv.h        config.guess  cpu           endmem.asm  init.asm    linux           md.psr       parsegen.cpp  vcache.asm  zloader.c  zpath.h
asm_call.h    config.h.in   debugasm.asm  gblhdr.h    initc.c     macros.mac      mmlib        patch.c       version.c   zloader.h  zstate.c
autogen.sh    config.sub    debugger.c    gblvars.h   input.psr   Makefile.check  net          SConstruct    video       zmovie.c   ztime.asm
cfg.psr       configure     dos           gui         install-sh  Makefile.in     numconv.h    tools         win         zmovie.h   ztimec.c
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **./autogen.sh**
Generating build information using aclocal and autoconf...
./autogen.sh: 6: **sdl-config: not found**
aclocal: couldn't open directory `/share/aclocal': No such file or directory
configure.in:49: error: possibly undefined macro: AC_MSG_ERROR
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:101: error: possibly undefined macro: AM_PATH_SDL
configure.in:104: error: possibly undefined macro: AM_PATH_ZLIB
configure.in:109: error: possibly undefined macro: AM_PATH_LIBPNG
configure.in:228: error: possibly undefined macro: AM_ARCH_DETECT
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... no
configure: error: You need NASM installed to compile ZSNES
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **apt-get install sdl-config**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Unable to locate package sdl-config**
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **sdl-config**
[B]The program 'sdl-config' is currently not installed.  You can install it by typing:
apt-get install libsdl1.2-dev[/B]
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **apt-get install libsdl1.2-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaa1-dev libavahi-client-dev libavahi-common-dev libcaca-dev libesd0-dev libpulse-dev libslang2-dev
The following NEW packages will be installed:
  libaa1-dev libavahi-client-dev libavahi-common-dev libcaca-dev libesd0-dev libpulse-dev libsdl1.2-dev libslang2-dev
0 upgraded, 8 newly installed, 0 to remove and 1 not upgraded.
Need to get 2,754kB of archives.
After this operation, 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com/ubuntu/ maverick-security/main libavahi-common-dev amd64 0.6.27-2ubuntu3.1 [71.8kB]
Get:2 http://it.archive.ubuntu.com/ubuntu/ maverick/main libslang2-dev amd64 2.2.2-4ubuntu1 [600kB]
Get:3 http://security.ubuntu.com/ubuntu/ maverick-security/main libavahi-client-dev amd64 0.6.27-2ubuntu3.1 [38.2kB]
Get:4 http://it.archive.ubuntu.com/ubuntu/ maverick/main libaa1-dev amd64 1.4p5-38build1 [146kB]                                                                           
Get:5 http://it.archive.ubuntu.com/ubuntu/ maverick/main libcaca-dev amd64 0.99.beta17-1 [935kB]                                                                           
Get:6 http://it.archive.ubuntu.com/ubuntu/ maverick/main libesd0-dev amd64 0.2.41-7 [29.2kB]                                                                               
Get:7 http://it.archive.ubuntu.com/ubuntu/ maverick-updates/main libpulse-dev amd64 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 [66.3kB]                             
Get:8 http://it.archive.ubuntu.com/ubuntu/ maverick/main libsdl1.2-dev amd64 1.2.14-6ubuntu3 [868kB]                                                                       
Fetched 2,754kB in 26s (103kB/s)                                                                                                                                           
Selecting previously deselected package libslang2-dev.
(Reading database ... 190807 files and directories currently installed.)
Unpacking libslang2-dev (from .../libslang2-dev_2.2.2-4ubuntu1_amd64.deb) ...
Selecting previously deselected package libaa1-dev.
Unpacking libaa1-dev (from .../libaa1-dev_1.4p5-38build1_amd64.deb) ...
Selecting previously deselected package libavahi-common-dev.
Unpacking libavahi-common-dev (from .../libavahi-common-dev_0.6.27-2ubuntu3.1_amd64.deb) ...
Selecting previously deselected package libavahi-client-dev.
Unpacking libavahi-client-dev (from .../libavahi-client-dev_0.6.27-2ubuntu3.1_amd64.deb) ...
Selecting previously deselected package libcaca-dev.
Unpacking libcaca-dev (from .../libcaca-dev_0.99.beta17-1_amd64.deb) ...
Selecting previously deselected package libesd0-dev.
Unpacking libesd0-dev (from .../libesd0-dev_0.2.41-7_amd64.deb) ...
Selecting previously deselected package libpulse-dev.
Unpacking libpulse-dev (from .../libpulse-dev_1%3a0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1_amd64.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.14-6ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/gtkdialog.info.gz'
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libslang2-dev (2.2.2-4ubuntu1) ...
Setting up libaa1-dev (1.4p5-38build1) ...
Setting up libavahi-common-dev (0.6.27-2ubuntu3.1) ...
Setting up libavahi-client-dev (0.6.27-2ubuntu3.1) ...
Setting up libcaca-dev (0.99.beta17-1) ...
Setting up libesd0-dev (0.2.41-7) ...
Setting up libpulse-dev (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1) ...
Setting up libsdl1.2-dev (1.2.14-6ubuntu3) ...
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **./autogen.sh **
Generating build information using aclocal and autoconf...
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... no
configure: **error: You need NASM installed to compile ZSNES**
root@sbraz-netbook:/usr/src/zsnes_1_51/src#** apt-get install nasm**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nasm
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,051kB of archives.
After this operation, 3,076kB of additional disk space will be used.
Get:1 http://it.archive.ubuntu.com/ubuntu/ maverick/main nasm amd64 2.08.01-1 [1,051kB]
Fetched 1,051kB in 7s (139kB/s)                                                                                                                                            
Selecting previously deselected package nasm.
(Reading database ... 191840 files and directories currently installed.)
Unpacking nasm (from .../nasm_2.08.01-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/gtkdialog.info.gz'
Setting up nasm (2.08.01-1) ...
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **./autogen.sh **
Generating build information using aclocal and autoconf...
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... *** buffer overflow detected ***: tools/archopt terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f28fa9c8537]
/lib/libc.so.6(+0xfe3f0)[0x7f28fa9c73f0]
/lib/libc.so.6(+0xfd2a7)[0x7f28fa9c62a7]
tools/archopt[0x400b25]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7f28fa8e7d8e]
tools/archopt[0x400829]
======= Memory map: ========
00400000-00402000 r-xp 00000000 08:01 2938341                            /usr/src/zsnes_1_51/src/tools/archopt
00601000-00602000 r--p 00001000 08:01 2938341                            /usr/src/zsnes_1_51/src/tools/archopt
00602000-00603000 rw-p 00002000 08:01 2938341                            /usr/src/zsnes_1_51/src/tools/archopt
01173000-01194000 rw-p 00000000 00:00 0                                  [heap]
7f28fa6b3000-7f28fa6c8000 r-xp 00000000 08:01 2886                       /lib/libgcc_s.so.1
7f28fa6c8000-7f28fa8c7000 ---p 00015000 08:01 2886                       /lib/libgcc_s.so.1
7f28fa8c7000-7f28fa8c8000 r--p 00014000 08:01 2886                       /lib/libgcc_s.so.1
7f28fa8c8000-7f28fa8c9000 rw-p 00015000 08:01 2886                       /lib/libgcc_s.so.1
7f28fa8c9000-7f28faa43000 r-xp 00000000 08:01 9363                       /lib/libc-2.12.1.so
7f28faa43000-7f28fac42000 ---p 0017a000 08:01 9363                       /lib/libc-2.12.1.so
7f28fac42000-7f28fac46000 r--p 00179000 08:01 9363                       /lib/libc-2.12.1.so
7f28fac46000-7f28fac47000 rw-p 0017d000 08:01 9363                       /lib/libc-2.12.1.so
7f28fac47000-7f28fac4c000 rw-p 00000000 00:00 0 
7f28fac4c000-7f28fac6c000 r-xp 00000000 08:01 9371                       /lib/ld-2.12.1.so
7f28fae43000-7f28fae46000 rw-p 00000000 00:00 0 
7f28fae69000-7f28fae6c000 rw-p 00000000 00:00 0 
7f28fae6c000-7f28fae6d000 r--p 00020000 08:01 9371                       /lib/ld-2.12.1.so
7f28fae6d000-7f28fae6e000 rw-p 00021000 08:01 9371                       /lib/ld-2.12.1.so
7f28fae6e000-7f28fae6f000 rw-p 00000000 00:00 0 
7fffcd76b000-7fffcd78c000 rw-p 00000000 00:00 0                          [stack]
7fffcd7ff000-7fffcd800000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
failed
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... guessing i386
configure: WARNING: This is not what you want, use --target or force-arch
checking if you want crazy optimizations... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... no
checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no
checking whether sys/types.h defines makedev... no
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking sys/sysmacros.h usability... no
checking sys/sysmacros.h presence... yes
configure: WARNING: sys/sysmacros.h: present but cannot be compiled
configure: WARNING: sys/sysmacros.h:     check for missing prerequisite headers?
configure: WARNING: sys/sysmacros.h: see the Autoconf documentation
configure: WARNING: sys/sysmacros.h:     section "Present But Cannot Be Compiled"
configure: WARNING: sys/sysmacros.h: proceeding with the compiler's result
checking for sys/sysmacros.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h


ZSNES v1.51

SDL support                   Version 1.2.14
NASM support                  NASM version 2.08.01 compiled on Jun  5 2010
zlib support                  Version 1.2.3.4
PNG support                   Yes, version 1.2.44
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

**Configure complete, now type 'make' and pray.**

root@sbraz-netbook:/usr/src/zsnes_1_51/src# 
```

unfortunately for me:
```
root@sbraz-netbook:/usr/src/zsnes_1_51/src# **make**
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=i386 -O3 -fomit-frame-pointer -s -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
[B]tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set[/B]
make: *** [tools/fileutil.o] Error 1
```

which leads to this:
[http://board.zsnes.com/phpBB3/viewtopic.php?f=3&t=13992](http://board.zsnes.com/phpBB3/viewtopic.php?f=3&t=13992)

no 64-bit distro support.... :( very sad.

---

### Post by Zill on 2011-08-23
> **Paqman said:**
> ...I haven't compiled anything from source in years.
+1

I really can't see any advantage in doing things the hard way.  ;-)

Unless you need to install something exotic a simple "*sudo apt-get install packagename*" usually works for me.

If I wish to keep an eye on any dependencies then the Synaptic package manager is a fantastic GUI for apt-get.

Otherwise, the simplicity of the Ubuntu Software Center is perfect for newbies.

Compiling from source is really not desirable for *most* users and will certainly cause more problems than it solves for newbies, particularly when they almost inevitably end up in "dependency hell". :-(

---

### Post by sbraz on 2011-08-23
> **Zill said:**
> I really can't see any advantage in doing things the hard way.  ;-)
i totally agree on some levels but there are exeptions, in my case:
**fahmon** which is an utility to check folding@home progresses doesn't have a ppa.

broadcom STA driver from the repository doesn't compile with kernel 3.0+, so i compiled it from source and i've discovered it works a lot better this way with all due respect to "hardware drivers" and "dkms", wl module loads a lot earlier so the connection is established before i see the desktop.

often the latest stable version of some apps doesn't reside in any repository.

it's just a matter of getting the hang of it. :)
i'm still learning btw. :D

---

### Post by PayPaul on 2011-09-27
> **anewguy said:**
> What specifically did the readme or install text say to do?  The normal procedure is to:

- unpack the file you downloaded.  This usually creates a subfolder that usually has the name in it somewhere - for example, if you downloaded "mystuff", then unpacked it, it usually creates a folder with "mystuff" in the name

- cd to the newly created folder - in the example above "mystuff"

- configure (it's probably something like ./configure)

- make

- sudo make install

There are also some prerequisite packages to install - build-essential is the main package you must have installed.  Others vary.

So, please post back what the install or readme text tells you to do.

Dave ;)

I'm trying to compile from source code the fractal program Quat. I started off with the ./configure command as you posted and got what looked promising until the very last line..

```
paulw@ubuntu:~/quat-1.20$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) mawk
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
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
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for memmove... yes
checking for memset... yes
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtod... yes
checking for strtol... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether the C compiler supports -Wall... yes
checking whether the C compiler supports -O3... yes
checking whether the C compiler supports -ffast-math... yes
checking for library containing pow... -lm
checking for floor... yes
checking for pow... yes
checking for sqrt... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
configure: error: [COLOR=Red]Library 'zlib' is required[/COLOR], aborting.
paulw@ubuntu:~/quat-1.20$ 

```Ick. How do I get the "zlib" library? Something to do with my version of Ubuntu? 11.04 or some flaw in the source code?

---

### Post by sbraz on 2011-09-28
ahhhh cmon just **nano README** and google for "configure: error: Library 'zlib' is required, aborting." (without quotes)...

:evil:















:-k

ANYWAY:

there's a chance that this procedure fails but i have 2 ways to fix these errors:

1.) via command lind i'd do this:

```
sbraz@sbraz-netbook:~$ sudo -i
[sudo] password for sbraz: 
root@sbraz-netbook:~# apt-get install zlib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="red"]E: Unable to locate package zlib[/COLOR]
```

the easy fix failed... never fear, add an asterisk to the package name (DON'T install all the packages proposed by this method unless you want to for some reason):

```

root@sbraz-netbook:~# apt-get install zlib[COLOR="Red"]*****[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'zlib1g' for regex 'zlib*'

[............]

Note, selecting 'perl-modules' instead of 'libio-zlib-perl'
Note, selecting 'libruby' instead of 'libzlib-ruby'

[B]zlib1g is already the newest version.
zlib1g-**[COLOR="Red"]-dev[/COLOR]** is already the newest version.
zlib1g**[COLOR="Red"]-dev[/COLOR]** set to manually installed.
perl-modules is already the newest version.
The following extra packages will be installed:
  gambas2-gb-compress gambas2-gb-compress-bzlib2 gambas2-gb-compress-zlib
  gambas2-runtime gauche gauche-zlib ghc6 ghc6-doc ghc6-prof gnu-smalltalk
  gnu-smalltalk-common haskell-zlib-doc libbsd[COLOR="Red"]-dev[/COLOR] libbz2[COLOR="Red"]-dev[/COLOR]
  libcompress-raw-zlib-perl libcompress-zlib-perl libffi[COLOR="Red"]-dev[/COLOR] libgauche0
  libghc6-bzlib[COLOR="Red"]-dev[/COLOR] libghc6-bzlib-doc libghc6-bzlib-prof libghc6-zlib[COLOR="Red"]-dev[/COLOR]
  libghc6-zlib-doc libghc6-zlib-prof libgmp3[COLOR="Red"]-dev[/COLOR] libgmpxx4ldbl libgst7
  libio-compress-zlib-perl libjzlib-java libruby libruby1.8 libsigsegv0 slib
  zlib-bin zlib-gst zlib1g-dbg zlibc[/B]
Suggested packages:
  r5rs-doc gauche-doc gauche-gdbm haskell-doc gnu-smalltalk-doc libgmp3-doc
  libmpfr[COLOR="Red"]-dev[/COLOR]
The following NEW packages will be installed:
  gambas2-gb-compress gambas2-gb-compress-bzlib2 gambas2-gb-compress-zlib
  gambas2-runtime gauche gauche-zlib ghc6 ghc6-doc ghc6-prof gnu-smalltalk
  gnu-smalltalk-common haskell-zlib-doc libbsd[COLOR="Red"]-dev[/COLOR] libbz2[COLOR="Red"]-dev[/COLOR]
  libcompress-raw-zlib-perl libcompress-zlib-perl libffi[COLOR="Red"]-dev[/COLOR] libgauche0
  libghc6-bzlib[COLOR="Red"]-dev[/COLOR] libghc6-bzlib-doc libghc6-bzlib-prof libghc6-zlib[COLOR="Red"]-dev[/COLOR]
  libghc6-zlib-doc libghc6-zlib-prof libgmp3[COLOR="Red"]-dev[/COLOR] libgmpxx4ldbl libgst7
  libio-compress-zlib-perl libjzlib-java libruby libruby1.8 libsigsegv0 slib
  zlib-bin zlib-gst zlib1g-dbg zlibc
0 upgraded, 37 newly installed, 0 to remove and 1 not upgraded.
Need to get 119MB of archives.
After this operation, 719MB of additional disk space will be used.
[COLOR="red"]Do you want to continue [Y/n]? **^C**[/COLOR]
root@sbraz-netbook:~#
```

check for those [COLOR=RED]-dev[/COLOR] packets and install the one by one, purging it should **./configure** fail... rinse, repeat.

2.) the other way uses your favourite package manager; it is simpler but sometimes command line simplicity and rawness leads to better results:
[[IMG]http://img683.imageshack.us/img683/5440/zlib.th.png[/IMG]](http://imageshack.us/photo/my-images/683/zlib.png/)

once you get the hang of this method compiling becomes "friendly" as it should be. ;)

ah btw, YES sometimes sources downloaded from the net are *largely outdated* so they just can't be compiled unless you change something complicated but that happened to me very few times.


```
root@sbraz-netbook:/usr/src/quat/quat-1.20# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) mawk
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
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
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for memmove... yes
checking for memset... yes
checking for strchr... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtod... yes
checking for strtol... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether the C compiler supports -Wall... yes
checking whether the C compiler supports -O3... yes
checking whether the C compiler supports -ffast-math... yes
checking for library containing pow... -lm
checking for floor... yes
checking for pow... yes
checking for sqrt... yes
[B][COLOR="Red"]checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes[/COLOR][/B]
checking for gzopen in -lz... yes
[B][COLOR="red"]checking for fltk-config... no
configure: WARNING:
   'fltk-config' not found. Compiling console version.
   If FLTK 1.1.x is not installed, please install it first if you want to
   compile the GUI version (strongly recommended).
   If FLTK 1.1.x is installed, and 'fltk-config' is not in your path, use
   the variable 'FLTK' in the configure command. Example:
   ./configure FLTK=/usr/local/fltk-1.1.0/bin/fltk-config[/COLOR][/B]
checking for select... yes
checking whether time.h and sys/time.h may both be included... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for memory.h... (cached) yes
checking conio.h usability... no
checking conio.h presence... no
checking for conio.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating kernel/Makefile
config.status: creating gui/Makefile
config.status: creating config.h
config.status: executing default-1 commands
root@sbraz-netbook:/usr/src/quat/quat-1.20#
```

still something missing... i can't find the package... what if i just type **fltk-config**?

```
root@sbraz-netbook:/usr/src/quat/quat-1.20# fltk-config
The program 'fltk-config' is currently not installed.  You can install it by typing:
apt-get install libfltk1.1-dev
```



:)

---

