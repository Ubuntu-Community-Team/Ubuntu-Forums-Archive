---
title: "Configure/compile errors"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by mslate on 2009-06-30
In trying to install a program ([Smoldyn]("http://www.smoldyn.org/")) from source, I am running into an error related to my compiler:

> configure: error: in `/home/burritoman/smoldyn-2.04':
configure: error: C preprocessor "/lib/cpp" fails sanity check

In my config.log file, I have:

> configure:3489: gcc  -c -g -O2  conftest.c >&5
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3496: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...
configure:3489: gcc -qlanglvl=extc89 -c -g -O2  conftest.c >&5
gcc: unrecognized option '-qlanglvl=extc89'
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3496: $? = 1
configure: failed program was:
| /* confdefs.h.  */
...

etc.
What is wrong with confdefs.h? Let me know if I should provide more info

---

### Post by linuxmagick on 2009-06-30
Have you tried ```
sudo apt-get install build-essential
```

---

### Post by mslate on 2009-06-30
```
burritoman@slaptop:~/smoldyn-2.04$ sudo apt-get install build-essential
[sudo] password for burritoman:
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

Yup, not sure what to do :( Any other suggestions?

---

### Post by linuxmagick on 2009-06-30
Not off the top of my head. If I think of anything else, I'll post it here or maybe someone else will have the answer you're looking for.

---

### Post by linuxmagick on 2009-06-30
My only other thought at the moment is to make sure that everything installed properly with build-essential.  You may want to try a **sudo apt-get install libc6-dev** and **sudo apt-get install gcc** just to make sure those packages are properly installed.

---

### Post by mslate on 2009-06-30
Both the GCC and libc6-dev packages are the newest versions.
It seems that the library addresses that the configure file's getting are incorrect.
Perhaps my directory location where stdio.h is located is irregular?

I ran locate stdio.h and this is what I got:

> /usr/include/c++/4.3/tr1/stdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

---

### Post by ~sHyLoCk~ on 2009-06-30
Do you have autoconf,automake installed? What are the contents of the extracted folder?
```
ls -l
```

---

### Post by kevdog on 2009-07-01
Im not getting these errors?  What Makefile are you using within the /source subfolder?

---

### Post by mslate on 2009-07-03
Sorry, just dropped the ball the last two days.

Re [COLOR="DarkRed"]Shylock[/COLOR]:

> burritoman@slaptop:~/smoldyn-2.04$ ls -l
total 1600
-rw-r--r--  1 burritoman burritoman  60073 2009-06-24 12:45 acinclude.m4
-rw-r--r--  1 burritoman burritoman 269894 2009-06-26 15:37 aclocal.m4
-rw-r--r--  1 burritoman burritoman      0 2009-06-05 13:52 AUTHORS
-rw-r--r--  1 burritoman burritoman      0 2009-06-05 13:52 ChangeLog
-rwxr-xr-x  1 burritoman burritoman  44878 2009-06-26 15:37 config.guess
-rw-r--r--  1 burritoman burritoman  32591 2009-06-30 14:18 config.log
-rwxr-xr-x  1 burritoman burritoman  33387 2009-06-26 15:37 config.sub
-rwxr-xr-x  1 burritoman burritoman 824746 2009-06-26 15:37 configure
-rw-r--r--  1 burritoman burritoman   5382 2009-06-26 12:44 configure.ac
-rw-r--r--  1 burritoman burritoman  35147 2008-02-04 05:53 COPYING
-rwxr-xr-x  1 burritoman burritoman  17867 2009-06-26 15:37 depcomp
drwxr-xr-x  2 burritoman burritoman   4096 2009-06-27 09:10 documentation
drwxr-xr-x 16 burritoman burritoman   4096 2009-06-26 15:38 examples
-rw-r--r--  1 burritoman burritoman   9512 2009-06-26 15:37 INSTALL
-rwxr-xr-x  1 burritoman burritoman  13620 2009-06-26 15:37 install-sh
-rw-r--r--  1 burritoman burritoman 199705 2008-08-29 15:27 ltmain.sh
-rw-r--r--  1 burritoman burritoman     41 2009-06-05 13:52 Makefile.am
-rw-r--r--  1 burritoman burritoman  20150 2009-06-26 15:37 Makefile.in
-rwxr-xr-x  1 burritoman burritoman  11135 2009-06-26 15:37 missing
-rw-r--r--  1 burritoman burritoman      0 2009-06-05 13:52 NEWS
-rw-r--r--  1 burritoman burritoman    548 2009-06-26 09:31 README
drwxr-xr-x  7 burritoman burritoman   4096 2009-06-27 09:00 source


Re [COLOR="DarkRed"]kevdog[/COLOR]

Why would I use a makefile from the source/ directory? I'm calling ./configure in /home/burritoman/smoldyn-2.04/ and it seems that the error is related to where I have my stdio.h file:

> burritoman@slaptop:~/smoldyn-2.04$ locate stdio.h
/home/burritoman/tiff-3.8.2/include/stdio.h
/home/burritoman/tiff-3.8.2/include/bits/stdio.h
[COLOR="DarkRed"]/usr/include/c++/4.3/tr1/stdio.h[/COLOR]
/usr/lib/perl/5.10.0/CORE/nostdio.h


Do you guys have something different?

---

### Post by mslate on 2009-07-03
I tried compiling a different program from source using configure/make/make install and I'm getting an identical error after using "./configure" command.

I know this is a wall of text, but perhaps the config.log file will be helpful:

> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = slaptop
uname -m = i686
uname -r = 2.6.28-11-generic
uname -s = Linux
uname -v = #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2037: checking for a BSD-compatible install
configure:2093: result: /usr/bin/install -c
configure:2104: checking whether build environment is sane
configure:2147: result: yes
configure:2175: checking for a thread-safe mkdir -p
configure:2214: result: /bin/mkdir -p
configure:2227: checking for gawk
configure:2257: result: no
configure:2227: checking for mawk
configure:2243: found /usr/bin/mawk
configure:2254: result: mawk
configure:2265: checking whether make sets $(MAKE)
configure:2286: result: yes
configure:2491: checking whether to enable maintainer-specific portions of Makefiles
configure:2500: result: no
configure:2525: checking for style of include used by make
configure:2553: result: GNU
configure:2623: checking for gcc
configure:2639: found /usr/bin/gcc
configure:2650: result: gcc
configure:2888: checking for C compiler version
configure:2895: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2898: $? = 0
configure:2905: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:2908: $? = 0
configure:2915: gcc -V >&5
gcc: '-V' option must have argument
configure:2918: $? = 1
configure:2941: checking for C compiler default output file name
configure:2968: gcc    conftest.c  >&5
configure:2971: $? = 0
configure:3009: result: a.out
configure:3026: checking whether the C compiler works
configure:3036: ./a.out
configure:3039: $? = 0
configure:3056: result: yes
configure:3063: checking whether we are cross compiling
configure:3065: result: no
configure:3068: checking for suffix of executables
configure:3075: gcc -o conftest    conftest.c  >&5
configure:3078: $? = 0
configure:3102: result: 
configure:3108: checking for suffix of object files
configure:3134: gcc -c   conftest.c >&5
configure:3137: $? = 0
configure:3160: result: o
configure:3164: checking whether we are using the GNU C compiler
configure:3193: gcc -c   conftest.c >&5
configure:3199: $? = 0
configure:3216: result: yes
configure:3221: checking whether gcc accepts -g
configure:3251: gcc -c -g  conftest.c >&5
configure:3257: $? = 0
configure:3356: result: yes
configure:3373: checking for gcc option to accept ISO C89
configure:3447: gcc  -c -g -O2  conftest.c >&5
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -qlanglvl=extc89 -c -g -O2  conftest.c >&5
gcc: unrecognized option '-qlanglvl=extc89'
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -qlanglvl=ansi -c -g -O2  conftest.c >&5
gcc: unrecognized option '-qlanglvl=ansi'
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -std -c -g -O2  conftest.c >&5
cc1: error: unrecognized command line option "-std"
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -Ae -c -g -O2  conftest.c >&5
<command-line>: error: missing '(' after predicate
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -Aa -D_HPUX_SOURCE -c -g -O2  conftest.c >&5
<command-line>: error: missing '(' after predicate
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3447: gcc -Xc -D__EXTENSIONS__ -c -g -O2  conftest.c >&5
gcc: unrecognized option '-Xc'
conftest.c:11:19: error: stdio.h: No such file or directory
conftest.c:12:23: error: sys/types.h: No such file or directory
conftest.c:13:22: error: sys/stat.h: No such file or directory
conftest.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
conftest.c:50: error: expected declaration specifiers or '...' before 'FILE'
configure:3453: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #include <stdarg.h>
| #include <stdio.h>
| #include <sys/types.h>
| #include <sys/stat.h>
| /* Most of the following tests are stolen from RCS 5.7's src/conf.sh.  */
| struct buf { int x; };
| FILE * (*rcsopen) (struct buf *, struct stat *, int);
| static char *e (p, i)
|      char **p;
|      int i;
| {
|   return p[i];
| }
| static char *f (char * (*g) (char **, int), char **p, ...)
| {
|   char *s;
|   va_list v;
|   va_start (v,p);
|   s = g (p, va_arg (v,int));
|   va_end (v);
|   return s;
| }
| 
| /* OSF 4.0 Compaq cc is some sort of almost-ANSI by default.  It has
|    function prototypes and stuff, but not '\xHH' hex character constants.
|    These don't provoke an error unfortunately, instead are silently treated
|    as 'x'.  The following induces an error, until -std is added to get
|    proper ANSI mode.  Curiously '\x00'!='x' always comes out true, for an
|    array size at least.  It's necessary to write '\x00'==0 to get something
|    that's true only with -std.  */
| int osf4_cc_array ['\x00' == 0 ? 1 : -1];
| 
| /* IBM C 6 for AIX is almost-ANSI by default, but it replaces macro parameters
|    inside strings and character constants.  */
| #define FOO(x) 'x'
| int xlc6_cc_array[FOO(a) == 'x' ? 1 : -1];
| 
| int test (int i, double x);
| struct s1 {int (*f) (int a);};
| struct s2 {int (*f) (double a);};
| int pairnames (int, char **, FILE *(*)(struct buf *, struct stat *, int), int, int);
| int argc;
| char **argv;
| int
| main ()
| {
| return f (e, argv, 0) != argv[0]  ||  f (e, argv, 1) != argv[1];
|   ;
|   return 0;
| }
configure:3479: result: unsupported
configure:3496: checking dependency style of gcc
configure:3587: result: none
configure:3648: checking for ranlib
configure:3664: found /usr/bin/ranlib
configure:3675: result: ranlib
configure:3708: checking for bison
configure:3738: result: no
configure:3708: checking for yacc
configure:3738: result: no
configure:3758: checking for flex
configure:3788: result: no
configure:3758: checking for lex
configure:3788: result: no
configure:3846: checking for gcc
configure:3873: result: gcc
configure:4111: checking for C compiler version
configure:4118: gcc --version >&5
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4121: $? = 0
configure:4128: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
configure:4131: $? = 0
configure:4138: gcc -V >&5
gcc: '-V' option must have argument
configure:4141: $? = 1
configure:4144: checking whether we are using the GNU C compiler
configure:4196: result: yes
configure:4201: checking whether gcc accepts -g
configure:4336: result: yes
configure:4353: checking for gcc option to accept ISO C89
configure:4459: result: unsupported
configure:4476: checking dependency style of gcc
configure:4567: result: none
configure:4660: checking build system type
configure:4678: result: i686-pc-linux-gnulibc1
configure:4700: checking host system type
configure:4715: result: i686-pc-linux-gnulibc1
configure:4737: checking for a sed that does not truncate output
configure:4793: result: /bin/sed
configure:4796: checking for grep that handles long lines and -e
configure:4870: result: /bin/grep
configure:4875: checking for egrep
configure:4953: result: /bin/grep -E
configure:4969: checking for ld used by gcc
configure:5036: result: /usr/bin/ld
configure:5045: checking if the linker (/usr/bin/ld) is GNU ld
configure:5060: result: yes
configure:5065: checking for /usr/bin/ld option to reload object files
configure:5072: result: -r
configure:5090: checking for BSD-compatible nm
configure:5139: result: /usr/bin/nm -B
configure:5143: checking whether ln -s works
configure:5147: result: yes
configure:5154: checking how to recognise dependent libraries
configure:5330: result: pass_all
configure:5564: checking how to run the C preprocessor
configure:5604: gcc -E  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5604: gcc -E  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5604: gcc -E -traditional-cpp  conftest.c
conftest.c:13: error: assert.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5604: gcc -E -traditional-cpp  conftest.c
conftest.c:13: error: assert.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5604: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5604: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5610: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5680: result: /lib/cpp
configure:5709: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5715: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5709: /lib/cpp  conftest.c
In file included from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:11,
                 from conftest.c:11:
/usr/lib/gcc/i486-linux-gnu/4.3.3/include-fixed/limits.h:122:61: error: limits.h: No such file or directory
configure:5715: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "snort"
| #define VERSION "2.8.4.1"
| /* end confdefs.h.  */
| #ifdef __STDC__
| # include <limits.h>
| #else
| # include <assert.h>
| #endif
| 		     Syntax error
configure:5777: error: C preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnulibc1
ac_cv_c_compiler_gnu=yes
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_GREP=/bin/grep
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP=/lib/cpp
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_cc_c89=no
ac_cv_prog_cc_g=yes
ac_cv_prog_make_make_set=yes
am_cv_CC_dependencies_compiler_type=none
am_cv_prog_cc_stdc=
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_SED=/bin/sed
lt_cv_prog_gnu_ld=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run aclocal-1.10'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run autoconf'
AUTOHEADER='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run autoheader'
AUTOMAKE='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run automake-1.10'
AWK='mawk'
CC='gcc'
CCDEPMODE='depmode=none'
CFLAGS='-g -O2'
CPP='/lib/cpp'
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR='.deps'
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
F77=''
FFLAGS=''
GREP='/bin/grep'
HAVE_DYNAMIC_PLUGINS_FALSE=''
HAVE_DYNAMIC_PLUGINS_TRUE=''
HAVE_SUP_IP6_FALSE=''
HAVE_SUP_IP6_TRUE=''
HAVE_TARGET_BASED_FALSE=''
HAVE_TARGET_BASED_TRUE=''
INCLUDES=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LEX='none'
LIBOBJS=''
LIBPRELUDE_CFLAGS=''
LIBPRELUDE_CONFIG=''
LIBPRELUDE_CONFIG_PREFIX=''
LIBPRELUDE_LDFLAGS=''
LIBPRELUDE_LIBS=''
LIBPRELUDE_PREFIX=''
LIBPRELUDE_PTHREAD_CFLAGS=''
LIBS=''
LIBTOOL=''
LN_S='ln -s'
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/burritoman/snort-2.8.4.1/missing --run makeinfo'
OBJEXT='o'
PACKAGE='snort'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
RANLIB='ranlib'
SED='/bin/sed'
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='2.8.4.1'
YACC='none'
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE='#'
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnulibc1'
build_alias=''
build_cpu='i686'
build_os='linux-gnulibc1'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
extra_incl=''
host='i686-pc-linux-gnulibc1'
host_alias=''
host_cpu='i686'
host_os='linux-gnulibc1'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/burritoman/snort-2.8.4.1/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE "snort"
#define VERSION "2.8.4.1"

configure: exit 1


This also may be of concern:

> burritoman@slaptop:~/smoldyn-2.04$ whereis stdio.h
stdio:

It's nowhere?!?

---

### Post by ~sHyLoCk~ on 2009-07-03
I see there's a README file, that doesn't give you any ideas? Go to synaptic and see if you have these installed:~ gcc, gcc-cpp,g++ and gcc-c++ and then just do ```
make
``` and see what happens. If things go fine do ```
sudo make install
```

---

### Post by mslate on 2009-07-03
> burritoman@slaptop:~/smoldyn-2.04$ make
make: *** No targets specified and no makefile found.  Stop.
burritoman@slaptop:~/smoldyn-2.04$ cd source/
burritoman@slaptop:~/smoldyn-2.04/source$ make
make: *** No targets specified and no makefile found.  Stop.


The README file just says what files were in the download. The problem more likely relates to my compiler setup since I'm having this issue with another program I'm trying to configure and make. It throws the same "sanity check" error while using the configure command:

> checking how to run the C preprocessor... /lib/cpp
configure: error: C preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


---

### Post by mc4man on 2009-07-04
What normally should be found is /usr/include/stdio.h (installed by libc6-dev
why don't you manually browse there and ck. if present.

If not you could try reinstalling libc6-dev, (Removing it would also remove many of your -dev packages

Never tried kubuntu 9.04. maybe something specific to it ...? ) dl'ing iso now, will test the livecd

---

### Post by mslate on 2009-07-04
It shouldn't matter that it's in a lower directory than /usr/include/ right?

> burritoman@slaptop:/usr/include$ locate stdio.h
/home/burritoman/tiff-3.8.2/include/stdio.h
/home/burritoman/tiff-3.8.2/include/bits/stdio.h
**/usr/include/c++/4.3/tr1/stdio.h**
/usr/lib/perl/5.10.0/CORE/nostdio.h

burritoman@slaptop:/usr/include$ ls -l
total 224                             
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 asm
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 asm-generic
drwxr-xr-x  3 root root  4096 2009-06-30 14:16 c++        
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 drm        
-rw-r--r--  1 root root  2703 2008-06-17 05:09 expat_config.h
-rw-r--r--  1 root root  3364 2008-06-17 05:09 expat_external.h
-rw-r--r--  1 root root 40339 2008-06-17 05:09 expat.h         
drwxr-xr-x  2 root root  4096 2009-06-30 14:17 fontconfig      
drwxr-xr-x  3 root root  4096 2009-06-30 14:17 freetype2       
-rw-r--r--  1 root root  3890 2009-04-23 05:26 ft2build.h      
drwxr-xr-x  3 root root  4096 2009-06-30 14:17 GL              
drwxr-xr-x 19 root root 12288 2009-07-02 09:55 linux           
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 mtd             
-rw-r--r--  1 root root 11690 2008-11-13 07:10 pciaccess.h     
drwxr-xr-x  2 root root  4096 2009-06-30 14:17 pixman-1        
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 rdma            
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 sound           
drwxr-xr-x  2 root root  4096 2009-07-02 09:55 video           
drwxr-xr-x 12 root root  4096 2009-06-30 14:17 X11             
drwxr-xr-x  2 root root  4096 2009-06-30 14:17 xcb             
drwxr-xr-x  2 root root  4096 2009-06-30 14:17 xorg            
-rw-r--r--  1 root root 12217 2009-03-18 10:08 zconf.h         
-rw-r--r--  1 root root   388 2009-03-18 10:08 zlibdefs.h      
-rw-r--r--  1 root root 68091 2009-03-18 10:08 zlib.h


I'll try reinstalling libc6-dev anyway

---

### Post by mc4man on 2009-07-04
> It shouldn't matter that it's in a lower directory than /usr/include/ right?

It should be in /usr/include

On a livecd right now, libc6-dev is installed by default 

> ubuntu@ubuntu:~$ locate stdio.h
[COLOR="Blue"]/usr/include/stdio.h[/COLOR]
/usr/include/bits/stdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h


I'll try your source, need a few min. to get adjusted to kubuntu (foreign is an severe understatement

---

### Post by mslate on 2009-07-04
RE mc4man:

Hey, I appreciate it, I guess my install (from a torrented ISO) was pretty limited. I reinstalled libc6-dev and it did the trick. A whole bunch of standard header files that I should have had are now littering my /usr/include/ (in the best kind of way)

Thanks for all the help, it looks like both configure and make commands are now working!


CASE CLOSED!

---

### Post by mc4man on 2009-07-04
It  configured fine here also on the livecd (took me a few to find the download, use to an  actual desktop.

Looks like your good to go. (and I can go back to gnome

---

