---
title: "[SOLVED] Module Loading Problems MadWiFi"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-23
According to the FAQ from the Madwifo.org site:

[http://madwifi.org/wiki/FAQ/ModuleLoadProblems](http://madwifi.org/wiki/FAQ/ModuleLoadProblems)

How do I reinstall MADWIFI modules:

/usr/src/linux#

I would 

make

then make modules_install

and lastly

make install

so my first question is

which one or ones do I run these commands against, because, this is the output ls of /usr/src:

mark@Lexington:/usr/src$ ls
linux-headers-2.6.20-15          linux-headers-2.6.20-16
linux-headers-2.6.20-15-generic  linux-headers-2.6.20-16-generic

if there is a conflict between some or all of these "headers" how is that corrected?

Because, after trying I got:

Trying the Madwifi Problems Loading Modules ideas:


mark@Lexington:/usr/src/linux-headers-2.6.20-16$ sudo make
Password:
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function &#8216;usage&#8217;:
scripts/basic/fixdep.c:129: warning: implicit declaration of function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:129: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function &#8216;exit&#8217;
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;print_cmdline&#8217;:
scripts/basic/fixdep.c:138: warning: implicit declaration of function &#8216;printf&#8217;
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: &#8216;NULL&#8217; undeclared here (not in a function)
scripts/basic/fixdep.c: In function &#8216;grow_config&#8217;:
scripts/basic/fixdep.c:154: warning: implicit declaration of function &#8216;realloc&#8217;
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function &#8216;perror&#8217;
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;is_defined_config&#8217;:
scripts/basic/fixdep.c:172: warning: implicit declaration of function &#8216;memcmp&#8217;
scripts/basic/fixdep.c: In function &#8216;define_config&#8217;:
scripts/basic/fixdep.c:185: warning: implicit declaration of function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c: In function &#8216;use_config&#8217;:
scripts/basic/fixdep.c:204: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:218: warning: implicit declaration of function &#8216;tolower&#8217;
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:204: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_config_file&#8217;:
scripts/basic/fixdep.c:225: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function &#8216;ntohl&#8217;
scripts/basic/fixdep.c:242: warning: implicit declaration of function &#8216;isalnum&#8217;
scripts/basic/fixdep.c: In function &#8216;strrcmp&#8217;:
scripts/basic/fixdep.c:255: warning: implicit declaration of function &#8216;strlen&#8217;
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
scripts/basic/fixdep.c: In function &#8216;do_config_file&#8217;:
scripts/basic/fixdep.c:266: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function &#8216;open&#8217;
scripts/basic/fixdep.c:270: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:272: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:276: warning: implicit declaration of function &#8216;fstat&#8217;
scripts/basic/fixdep.c:278: warning: implicit declaration of function &#8216;close&#8217;
scripts/basic/fixdep.c:281: warning: implicit declaration of function &#8216;mmap&#8217;
scripts/basic/fixdep.c:281: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function &#8216;parse_config_file&#8217;
scripts/basic/fixdep.c:290: warning: implicit declaration of function &#8216;munmap&#8217;
scripts/basic/fixdep.c:266: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_dep_file&#8217;:
scripts/basic/fixdep.c:298: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function &#8216;strchr&#8217;
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:304: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:300: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: In function &#8216;print_deps&#8217;:
scripts/basic/fixdep.c:337: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:341: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:343: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:353: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function &#8216;parse_dep_file&#8217;
scripts/basic/fixdep.c:337: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: In function &#8216;traps&#8217;:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:372: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
mark@Lexington:/usr/src/linux-headers-2.6.20-16$ sudo make modules_install
if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map  2.6.20.3-ubuntu1; fi
mark@Lexington:/usr/src/linux-headers-2.6.20-16$ sudo make install
sh /usr/src/linux-headers-2.6.20-16/arch/i386/boot/install.sh 2.6.20.3-ubuntu1 arch/i386/boot/bzImage System.map "/boot"
sh: Can't open /usr/src/linux-headers-2.6.20-16/arch/i386/boot/install.sh
make[1]: *** [install] Error 2
make: *** [install] Error 2
mark@Lexington:/usr/src/linux-headers-2.6.20-16$

---

### Post by Ayuthia on 2007-07-23
I am not for sure exactly on what is leading you to your adventure on rebuilding the kernel and modules for MADWiFi, but you are missing some libraries.  One of them that you will need is build-essentials.

As for which version to use, you should type uname -r and it will show you which version you are currently using.

Have you tried the current modules to see if they work?

---

### Post by t4thfavor on 2007-07-23
I am not sure, but don't you need the kernel-source and not just the headers?

---

### Post by Mark_in_Hollywood on 2007-07-23
> **Ayuthia said:**
> I am not for sure exactly on what is leading you to your adventure on rebuilding the kernel and modules for MADWiFi, but you are missing some libraries.  One of them that you will need is build-essentials.

As for which version to use, you should type uname -r and it will show you which version you are currently using.

Have you tried the current modules to see if they work?

1) would syn. pkg. mgr. load the build-essentials?

2)   uname -r returns

2.6.20-16-386

and  

3)    As a noobie, I have no idea of what all has been tried by me. As you can see, from the above origin of this post/thread, I attempted a (I guess) compile of some module in /src/modules/2-6.20-16-386. I'm not trying to sound flip, here, I've tried literally dozens of ideas. None has worked. This is my 3rd or 4th post about resolving this problem, so, please bear with a fatigued human a little while longer.

I believe that didn't work from the error messages I see in the responses from the various make/make module/make install commands.

I've been told to try:

modprobe -a

which returned unknown module(s), etc.

I'm so all over the place with this, I'm willing to try everything (say: anything) but, have no clue as to what to do.  Honest injun!

---

### Post by Ayuthia on 2007-07-23
As t4thfavor said, you probably want the kernel source too.

> **Mark_in_Hollywood said:**
> 1) would syn. pkg. mgr. load the build-essentials?

Yes 

> **Mark_in_Hollywood said:**
> 3)    As a noobie, I have no idea of what all has been tried by me. As you can see, from the above origin of this post/thread, I attempted a (I guess) compile of some module in /src/modules/2-6.20-16-386. I'm not trying to sound flip, here, I've tried literally dozens of ideas. None has worked. This is my 3rd or 4th post about resolving this problem, so, please bear with a fatigued human a little while longer.

I am not for sure what your result will be, but if you do make a successful compile, you should be ok.  If you are using any nvidia drivers, you might have to reinstall it also.  I am not for sure about ATI graphic drivers because I have not been able to get my hands on one yet...

Good luck!

---

### Post by Mark_in_Hollywood on 2007-07-23
2nd attempt after build-essential was installed/re-installed

mark@Lexington:/usr/src/linux-headers-2.6.20-16$ modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-386/madwifi/ath_pci.ko): Operation not permitted


mark@Lexington:/usr/src/linux-headers-2.6.20-16$ sudo make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/lex.c
  SHIPPED scripts/genksyms/parse.h
  SHIPPED scripts/genksyms/keywords.c
  HOSTCC  scripts/genksyms/lex.o
  SHIPPED scripts/genksyms/parse.c
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/bin2c
[B]make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2[/B]

mark@Lexington:/usr/src/linux-headers-2.6.20-16$ ls
arch    debian   include  kernel                  Makefile  scripts   ubuntu
block   drivers  init     lib                     mm        security  usr
crypto  fs       ipc      linux-headers.revision  net       sound

mark@Lexington:/usr/src/linux-headers-2.6.20-16$ cd ..
mark@Lexington:/usr/src$ ls
linux-headers-2.6.20-15          linux-headers-2.6.20-16
linux-headers-2.6.20-15-generic  linux-headers-2.6.20-16-generic

mark@Lexington:/usr/src$ cd /usr/src/linux-headers-2.6.20-16-generic

mark@Lexington:/usr/src/linux-headers-2.6.20-16-generic$ sudo make
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/genksyms/lex.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
[B]make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2[/B]

---

### Post by Mark_in_Hollywood on 2007-07-25
THREAD CLOSED.

I've reinstalled Feisty.

---

