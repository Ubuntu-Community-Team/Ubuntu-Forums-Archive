---
title: "problem w/architecture?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by willy james on 2009-03-31
Hi all,

This is very strange.  I've taken a package manually from the site: 

[http://packages.debian.org/etch/amd64/ia32-libs/download](http://packages.debian.org/etch/amd64/ia32-libs/download)

...downloaded the *.DEB file, and want to unpack it with the GDebi package installer tool.  

No dice!  I've selected the AMD64 version, as per the 'system > system monitor' information.  Yet I still get this message:

Error: Wrong architecture 'amd64' 
ia32 shared libraries for use on amd64 and ia64 systems
This package contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Debian system running a 64-bit kernel. 

being a noobie-noob I am probably missing something.  
but what?  Will

---

### Post by davec64 on 2009-04-01
First off lets double chack your system, so in a terminal type:

```
 uname -a

```

and copy the reply here.

---

### Post by skymera on 2009-04-01
Are you running a 32bit or 64bit Ubuntu?

That package is for 64bit.

Run the command in the above post and we can go from there :)

---

### Post by willy james on 2009-04-02
> uname -a 

returns

Linux will-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

yes the system is 64-bit AMD Athlon(tm) 64X2 Dual Core Processor 5000+

helpful? Will

---

### Post by abyssius on 2009-04-02
> **willy james said:**
> > uname -a 

returns

Linux will-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

yes the system is 64-bit AMD Athlon(tm) 64X2 Dual Core Processor 5000+

helpful? Will

It looks like you installed the 32-bit version of Ubuntu. You can only use 32-bit software

---

### Post by willy james on 2009-04-02
Abyssius... you say "looks like" 32-bit.

any chance this provides conclusive answer one way or another?

will@will-desktop:/usr/lib$ getconf -a | grep BIT
CHAR_BIT                           8
LONG_BIT                           32
WORD_BIT                           32
LFS_CFLAGS                         -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
LFS_LINTFLAGS                      -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
XBS5_ILP32_OFFBIG_CFLAGS           -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
POSIX_V6_ILP32_OFFBIG_CFLAGS       -m32 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
FILESIZEBITS                       64

---

### Post by davec64 on 2009-04-03
> **willy james said:**
> > i686 GNU/Linux



Willy, you definitely are running the 32bit version of Ubuntu as denoted by the i686. Therefore you need the 32bit versions of software.

You need to change Ubuntu to 64bit (reinstall) to use the 64bit packages.

All the best

---

### Post by unikuser on 2009-04-03
> **abyssius said:**
> It looks like you installed the 32-bit version of Ubuntu. You can only use 32-bit software

You will have **x86_64** instead of i686 if it is 64bit. 

```
2.6.28-11-generic #38-Ubuntu SMP Fri Mar 27 10:01:17 UTC 2009 x86_64 GNU/Linux
```

---

### Post by hyper_ch on 2009-04-03
and why do you download packages from debian?

---

