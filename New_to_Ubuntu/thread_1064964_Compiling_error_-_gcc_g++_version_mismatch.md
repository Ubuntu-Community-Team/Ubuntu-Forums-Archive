---
title: "Compiling error - gcc g++ version mismatch?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by GreenRanger on 2009-02-09
Hello,

I'm sure this is a simple misconfiguration, but as I am rather new to linux and compiling thought I would reach out for help.  I'm trying to compile come code on Ubuntu 8.10 and am running into this error I can't seem to figure out.  I have installed the build-essentials but it seems like this code is expecting a different version of gcc.  Any ideas?  Thanks!

user@desktop:~/dtn-2.6.0$ sh configure -C
configure: loading cache config.cache
checking location of source directory... "/home/booz/dtn-2.6.0"
checking location of build directory... "/home/booz/dtn-2.6.0"
checking for a C compiler (trying gcc gcc-4.1 gcc-4.0 gcc-3.4 gcc-3.3)... 
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a C++ compiler (trying g++ g++-4.0 g++-4.0 g++-3.4 g++-3.3)... 
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether the C++ compiler works... yes
checking how to run the C preprocessor... gcc -E
checking for the version of the GNU C compiler... gcc
checking for the version of the GNU C++ compiler... g++
*** 
*** warning: C compiler version gcc doesn't equal
***          C++ compiler version g++
*** 
error: unsupported compiler version gcc

---

### Post by Temposs on 2009-02-09
The version of gcc that is installed on Ubuntu 8.10 is gcc 4.3.2. This configure script seems to check only as high as gcc 4.1. So, you could try changing the configure script so it doesn't give that error or find a newer version of this program that will check for gcc 4.3+

Give the output for me of this:

```
gcc --version
```

and

```
g++ --version
```

---

### Post by GreenRanger on 2009-02-09
Wow, thanks for the quick reply Temposs!  Here are the versions.

$ gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ g++ --version
g++ (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


I really don't need anything fancy on this desktop... should I just try downgrading GCC or even Ubuntu?  Here is a section of the configure script.  Should I add in 4.3 as a check?  The source code is located [http://sourceforge.net/project/showfiles.php?group_id=101657&package_id=281082](http://sourceforge.net/project/showfiles.php?group_id=101657&package_id=281082)

# -------------------------------------------------------------------------
# Configure gcc and find oasys
# -------------------------------------------------------------------------



                    if test ! -z "$host_alias" ; then
        TARGET=$host_alias
    elif test ! -z "$target_alias" ; then
        TARGET=$target_alias
    elif test ! -z "$target" ; then
        TARGET=$target
    else
        TARGET=native
    fi



                ac_with_cc=$CC

# Check whether --with-cc was given.
if test "${with_cc+set}" = set; then
  withval=$with_cc; ac_with_cc=$withval
fi


    ac_with_cxx=$CXX

# Check whether --with-cxx was given.
if test "${with_cxx+set}" = set; then
  withval=$with_cxx; ac_with_cxx=$withval
fi


    if test "x$ac_with_cc" = "x" ; then
        ac_try_cc="gcc gcc-4.1 gcc-4.0 gcc-3.4 gcc-3.3"
        ac_try_cxx="g++ g++-4.0 g++-4.0 g++-3.4 g++-3.3"
    else
        ac_try_cc=$ac_with_cc

	if test x"$ac_with_cxx" = x ; then
            ac_try_cxx=`echo $ac_with_cc | sed 's/cc/++/'`
	    { echo "$as_me:$LINENO: inferring C++ compiler '$ac_try_cxx' from C compiler setting" >&5
echo "$as_me: inferring C++ compiler '$ac_try_cxx' from C compiler setting" >&6;}
	else
	    ac_try_cxx=$ac_with_cxx
	fi

	CC=$ac_try_cc
	CXX=$ac_try_cxx
    fi

---

### Post by Temposs on 2009-02-09
hi GreenRanger,

I recommend that you should usually keep the version of software that Ubuntu gets installed for you. Then Ubuntu will be the most stable it can be. In this case, yes, try putting in a check for gcc version 4.3, and see what happens.

---

### Post by Temposs on 2009-02-09
EDIT: Disregard my advice above. See below.

Oh, you know what?

Ubuntu has gcc version 4.1 in the repositories too.

Just install that through synaptic. EDIT: Search for gcc in Synaptic, and you'll see Ubuntu has like 4 versions in the repositories. Get 4.1, and your configure script should work as is.

---

### Post by mmlab on 2009-11-11
Dear all:

I also have the same problem :(

How did you solve the problem ?

Could you give me the detail of the solution about this problem?

---

### Post by machko on 2010-10-24
Hi, can somebody help with this: ( using ubuntu 10.10)

root@server:/etc/ssh/mc-4.6.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

but...

root@server:/etc/ssh/mc-4.6.1# apt-get install gcc-4.5-base
Csomaglisták olvasása... Kész / Done
Függ&#337;ségi fa építése 
Állapot adatok olvasása... Kész / Done
gcc-4.5-base már a legújabb verzió. / you already have the newest version

and...

root@server:/etc/ssh/mc-4.6.1# gcc --version
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: apt-get install <selected package>

root@server:/etc/ssh/mc-4.6.1# g++ --version
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: apt-get install <selected package>

I don't get it, honestly - maybe thats because the 10.10 ubuntu ?

---

### Post by mc4man on 2010-10-24
gcc-4.5-base and gcc-4.4-base are installed by default, many packages depend on the 4.5 base -however the default gcc (dependency package gcc) in 10.10 is gcc-4.4

So just install gcc and g++ or go 
```
sudo apt-get install build-essential
```

If you want to use gcc-4.5 you can specific to the build (add to configure, makefile, whatever. (you must install gcc-4.5 manually

Anything that looks for gcc will use the default (gcc-4.4

---

