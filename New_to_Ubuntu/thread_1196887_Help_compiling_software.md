---
title: "Help compiling software"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ucamapping on 2009-06-25
I am attempting to compile an old, but robust, program called mapmaker/exp used in linkage mapping. I have obtained the source code, downloaded & installed build-essential, checkinstall,  & gcc. The makefile is written in c (from '93) so are these all I need?

Since I am a noob, I have simply scoured through the forums for help in installation.  However, the first step I have seen (./configure) does not work because no configure file is present; I believe the code comes pre-compiled. In anticipation in responses, I have navigated to correct directory...(cd ~/Desktop/mapmaker)

Based on the assumption that the code is pre-compiled, my next move was to use 'make.' I run these errors:
> 
cc -I./lib/ -D_SYS_SUNOS -c lib/memlib.c -o lib/memlib.o
In file included from /usr/include/stdio.h:822,
                 from lib/system.h:519,
                 from lib/memlib.c:19:
/usr/include/bits/sys_errlist.h:28: error: conflicting types for &#8216;sys_errlist&#8217;
lib/system.h:184: error: previous declaration of &#8216;sys_errlist&#8217; was here
In file included from lib/system.h:544,
                 from lib/memlib.c:19:
/usr/include/string.h:256: error: expected identifier or &#8216;(&#8217; before &#8216;int&#8217;
In file included from lib/memlib.c:19:
lib/system.h:596: error: conflicting types for &#8216;srandom&#8217;
/usr/include/stdlib.h:330: error: previous declaration of &#8216;srandom&#8217; was here
make: *** [lib/memlib.o] Error 1

Can someone help me make sense of this? Should the next move be to the fix the 'errors' or is there a problem in regards to dependencies in the old c?

Thanks in advance!

---

### Post by oldos2er on 2009-06-25
Can you post the output of this command?
```
ls ~/Desktop/mapmaker
```

---

### Post by ucamapping on 2009-06-25
> aux          ghostscript.tar.Z  mapm3-sparc  READ.ME      sample.xdata
CHANGE.ME    INSTALL.ME         mouse.in     sample.in    sample.xmaps
COVER.ME     lib                mouse.prep   sample.inp   sample.xqtls
dist         Makefile           mouse.raw    sample.inq   sample.xtraits
FEED.ME      mapm               quant        sample.qtls  sun
ghostscript  mapm3-source.tar   readline     sample.raw   WANT.ME

Sample and mouse folders are for use within the program

Thanks for the quick reply

---

### Post by oldos2er on 2009-06-25
Have you read READ.ME and/or INSTALL.ME? I'm not sure what the errors you're seeing mean.

---

### Post by ucamapping on 2009-06-25
I have perused them both, and the only aid given for compiling on another system within either document is the statement

 "Source code (in "C") is also available by anonymous FTP which you may be able 
to compile and run on other platforms."

which has already been done. Not much other documentation other than to explain how to install using the executable.

---

