---
title: "Trying to compile BLT, can't find tcl configuration..."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Kulanga on 2009-01-10
Im trying to install moodss in my ubuntu 8.1 box. I installed Active Tcl and then tried to install BLT by compiling using './configure' but ran into following error.

"checking for Tcl configuration... configure: WARNING: Can't find Tcl configuration definitions"
I installed all the devs by sudo apt-get install expect-dev and tried with configure command similar to following 
./configure --with-tclconfig=/opt/ActiveTcl8.5/lib/tclConfig.sh --with-tkconfig=/opt/ActiveTcl8.5/lib/tclConfig.sh

but had no luck so far... Can somebody help me out on this?? Thanks in advance..

---

### Post by albinootje on 2009-01-10
> **Kulanga said:**
> Im trying to install moodss in my ubuntu 8.1 box. 
-- cut --
but had no luck so far... 

The moodss software is from 2006.
Compiling on 8.10 might be too hard.

I just tested the following on 8.10.
Downloaded from [http://moodss.sourceforge.net/](http://moodss.sourceforge.net/) at this section :
> 
Packages:

    * standalone Linux AMD/Intel 64 bit and 32 bit binaries (for glibc 2.4 based systems), complete with all required software (including SQLite database and R statistical engine), installs in a sub-directory: 


Tried the first two lines of the instructions.
> 
$ tar -xjf moodss-21.5.i386.tar.bz2            # unpack it
$ moodss-21.5/moodss.sh cpustats memstats      # now use it

And that seemed to work fine.

---

### Post by Bachstelze on 2009-01-10
```
sudo apt-get install pkg-config tcl-dev
```

---

### Post by Kulanga on 2009-01-11
I tried the standalone installation but couldn't run the Predictor tool (couldn't set the path using tools ->preferences). Thats why I tried the permenent installation. I dont mind using the standalone if i can use the Predictor tool. As per the documentation, this should be possible( since it includes the R statistical engine). But no luck for me so far..(moodss is up and running using the standalone, though).Glad if you can help me on this.. Thanks in advance..

---

### Post by albinootje on 2009-01-11
> **Kulanga said:**
> I tried the standalone installation but couldn't run the Predictor tool (couldn't set the path using tools ->preferences). Thats why I tried the permenent installation. I dont mind using the standalone if i can use the Predictor tool. As per the documentation, this should be possible( since it includes the R statistical engine). But no luck for me so far..(moodss is up and running using the standalone, though).Glad if you can help me on this.. Thanks in advance..

So, you applied the apt-get suggestion in the other comment, and continued compiling ? 
What are the new errors ?
A 
```

make clean

```
in the directory that you're compiling in, can sometimes be useful.
Also when running "configure" a log file is produces in the same directory, which sometimes can reveal more information what the configure script is exactly looking for.

---

### Post by Kulanga on 2009-01-11
yes, but its the same error....
following is the log file. hope would be useful..

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:705: checking host system type
configure:726: checking target system type
configure:744: checking build system type
configure:771: checking for wish
configure:837: checking which C compiler
configure:852: checking for gcc
configure:965: checking whether the C compiler (gcc  ) works
configure:981: gcc -o conftest    conftest.c  1>&5
configure:1007: checking whether the C compiler (gcc  ) is a cross-compiler
configure:1012: checking whether we are using GNU C
configure:1021: gcc -E conftest.c
configure:1040: checking whether gcc accepts -g
configure:1095: checking how to run the C preprocessor
configure:1116: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1210: checking default compiler flags
configure:1240: checking for Cygwin environment
configure:1256: gcc -c -O6  conftest.c 1>&5
configure: In function 'main':
configure:1252: error: '__CYGWIN32__' undeclared (first use in this function)
configure:1252: error: (Each undeclared identifier is reported only once
configure:1252: error: for each function it appears in.)
configure: failed program was:
#line 1245 "configure"
#include "confdefs.h"

int main() {

#ifndef __CYGWIN__
#define __CYGWIN__ __CYGWIN32__
#endif
return __CYGWIN__;
; return 0; }
configure:1302: checking for mawk
configure:1343: checking for a BSD compatible install
configure:1398: checking for ranlib
configure:1426: checking whether ln -s works
configure:1453: checking for main in -lsocket
configure:1468: gcc -o conftest -O6   conftest.c -lsocket   1>&5
/usr/bin/ld: cannot find -lsocket
collect2: ld returned 1 exit status
configure: failed program was:
#line 1461 "configure"
#include "confdefs.h"

int main() {
main()
; return 0; }
configure:1496: checking for main in -lnsl
configure:1511: gcc -o conftest -O6   conftest.c -lnsl   1>&5
configure:1539: checking for main in -lm
configure:1554: gcc -o conftest -O6   conftest.c -lm  -lnsl  1>&5
configure:1588: checking for ANSI C header files
configure:1601: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1668: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure: In function 'main':
configure:1663: warning: incompatible implicit declaration of built-in function 'exit'
configure:1692: checking for sys/wait.h that is POSIX.1 compatible
configure:1713: gcc -c -O6  conftest.c 1>&5
configure:1734: checking whether time.h and sys/time.h may both be included
configure:1748: gcc -c -O6  conftest.c 1>&5
configure:1773: checking for inttypes.h
configure:1783: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1820: checking for limits.h
configure:1830: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1820: checking for sys/param.h
configure:1830: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1860: checking for string.h
configure:1870: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1860: checking for ctype.h
configure:1870: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1900: checking for errno.h
configure:1910: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1900: checking for float.h
configure:1910: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1900: checking for math.h
configure:1910: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1900: checking for ieeefp.h
configure:1910: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1906:20: error: ieeefp.h: No such file or directory
configure: failed program was:
#line 1905 "configure"
#include "confdefs.h"
#include <ieeefp.h>
configure:1940: checking for sys/time.h
configure:1950: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1940: checking for waitflags.h
configure:1950: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1946:23: error: waitflags.h: No such file or directory
configure: failed program was:
#line 1945 "configure"
#include "confdefs.h"
#include <waitflags.h>
configure:1940: checking for sys/wait.h
configure:1980: checking for malloc.h
configure:1990: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:1980: checking for memory.h
configure:1990: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:2020: checking for setjmp.h
configure:2030: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:2112: checking for stdlib.h
configure:2122: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:2112: checking for unistd.h
configure:2122: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:2155: checking for size_t
configure:2188: checking for pid_t
configure:2222: checking whether union wait is defined correctly
configure:2245: gcc -c -O6  conftest.c 1>&5
configure:2274: checking whether byte ordering is bigendian
configure:2292: gcc -c -O6  conftest.c 1>&5
configure:2307: gcc -c -O6  conftest.c 1>&5
configure: In function 'main':
configure:2302: error: 'not' undeclared (first use in this function)
configure:2302: error: (Each undeclared identifier is reported only once
configure:2302: error: for each function it appears in.)
configure:2302: error: expected ';' before 'big'
configure: failed program was:
#line 2296 "configure"
#include "confdefs.h"
#include <sys/types.h>
#include <sys/param.h>
int main() {

#if BYTE_ORDER != BIG_ENDIAN
 not big endian
#endif
; return 0; }
configure:2364: checking size of int
configure:2383: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure: In function 'main':
configure:2377: warning: incompatible implicit declaration of built-in function 'exit'
configure:2403: checking size of long
configure:2422: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure: In function 'main':
configure:2416: warning: incompatible implicit declaration of built-in function 'exit'
configure:2442: checking size of long long
configure:2461: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure: In function 'main':
configure:2455: warning: incompatible implicit declaration of built-in function 'exit'
configure:2481: checking size of void *
configure:2500: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure: In function 'main':
configure:2494: warning: incompatible implicit declaration of built-in function 'exit'
configure:2538: checking for strdup
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2550: warning: conflicting types for built-in function 'strdup'
configure:2538: checking for strcasecmp
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2550: warning: conflicting types for built-in function 'strcasecmp'
configure:2538: checking for strncasecmp
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2550: warning: conflicting types for built-in function 'strncasecmp'
configure:2538: checking for drand48
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2538: checking for srand48
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2538: checking for finite
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2550: warning: conflicting types for built-in function 'finite'
configure:2538: checking for isnan
configure:2566: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
configure:2550: warning: conflicting types for built-in function 'isnan'
configure:2593: checking for isfinite
configure:2610: gcc -o conftest -O6   conftest.c -lm -lnsl  1>&5
/tmp/ccSfgb0l.o: In function `main':
conftest.c:(.text+0x17): undefined reference to `isfinite'
collect2: ld returned 1 exit status
configure: failed program was:
#line 2598 "configure"
#include "confdefs.h"
#include <math.h>
int main() {

double x = 1.0;
if (isfinite(x)) {
   return 0;
}

; return 0; }
configure:2639: checking whether DBL_EPSILON is defined in float.h
configure:2724: checking whether declaration is needed for strdup
configure:2765: checking whether declaration is needed for drand48
configure:2806: checking whether declaration is needed for srand48
configure:2847: checking whether declaration is needed for j1
configure:2897: checking for X
configure:2964: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:3040: gcc -o conftest -O6   conftest.c -lXt -lm -lnsl  1>&5
configure:3134: checking for tclConfig.sh
configure:3230: checking for tkConfig.sh

---

### Post by albinootje on 2009-01-11
Just did the following ugly workaround, to see how far the compiling would get with that :
```

sudo cp /usr/include/tcl/*.h /usr/include/

```
> 
~/moodss-21.5$ make
LIBRARY="/usr/lib/libtclstub`echo 'puts $tcl_version' | tclsh`.a"; export LIBRARY;\
		rm -f libtclstub.a; test -f $LIBRARY && ln -s $LIBRARY libtclstub.a || ln -s /usr/lib/libtclstub.a libtclstub.a
gcc -shared -fPIC -DUSE_TCL_STUBS -O2  -o packlibs/libfilesystem.so.1.1 packlibs/filesystem.c libtclstub.a
gcc -shared -fPIC -DUSE_TCL_STUBS -O2  -o packlibs/libnetwork.so.1.23 packlibs/network.c libtclstub.a 
gcc -shared -fPIC -DUSE_TCL_STUBS -O2  -o packlibs/liblogging.so.1.0 packlibs/logging.c libtclstub.a
packlibs/logging.c: In function ‘system’:
packlibs/logging.c:30: warning: format not a string literal and no format arguments

> 
~/moodss-21.5$ ./moodss random
can't find package Tktable 2.7
    while executing
"package require Tktable 2.7"
    (file "./moodss" line 18676)

```

~/moodss-21.5$ apt-cache search tktable
libtktable2.9 - Table extension for Tcl/Tk

```
```

~/moodss-21.5$ sudo apt-get install libtktable2.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstlport4.6ldbl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libtktable2.9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 121kB of archives.
After this operation, 332kB of additional disk space will be used.
Get:1 http://nl.archive.ubuntu.com intrepid/universe libtktable2.9 2.9+cvs20060727-2 [121kB]
Fetched 121kB in 0s (358kB/s)  
Selecting previously deselected package libtktable2.9.
(Reading database ... 177084 files and directories currently installed.)
Unpacking libtktable2.9 (from .../libtktable2.9_2.9+cvs20060727-2_i386.deb) ...
Processing triggers for man-db ...
Setting up libtktable2.9 (2.9+cvs20060727-2) ...

~/moodss-21.5$ ./moodss random

```

.. Starts up fine.
Do you need the moomps binaries too ?

Can you try the same as above ?

---

### Post by Kulanga on 2009-01-11
Frankly, i cant understand what you have done here.You are working inside the 'moodss-21.5' directory.That is supposed to be the standalone application directory. Its working fine for me except for the Predictor tool. The config file i posted earlier was generated inside the BLT folder while im trying to compile BLT after installing Active Tcl. I installed both these b'cos i was tring to compile the moodss (not the standalone installation)
I dont need a moomps installation. moodss wil do.. with the Predictor tool working.. Thanks for your effort so far..:)

---

### Post by albinootje on 2009-01-11
> **Kulanga said:**
> Frankly, i cant understand what you have done here.

I tried to show you that compiling the required development software is really not needed.
The webpage says "always use latest" packages, but for software that had its last version released in 2006 you can take this with a large grain of salt.

> 
You are working inside the 'moodss-21.5' directory.That is supposed to be the standalone application directory. Its working fine for me except for the Predictor tool. The config file i posted earlier was generated inside the BLT folder while im trying to compile BLT after installing Active Tcl. I installed both these b'cos i was tring to compile the moodss (not the standalone installation)
I dont need a moomps installation. moodss wil do.. with the Predictor tool working.. Thanks for your effort so far..:)

OK, i've now also tried with installing (sudo make install), and that works too.
Again, please forget about compiling blt, and install the blt-dev package right away.

About the Predictor tool. See attached screenshot.
It looks like it needs additional (statistical?) software, like "R" before it will work.

See also :
[http://jfontain.free.fr/moodss.htm#menus.tools.predictor](http://jfontain.free.fr/moodss.htm#menus.tools.predictor)
[http://jfontain.free.fr/statistics.htm](http://jfontain.free.fr/statistics.htm)

---

