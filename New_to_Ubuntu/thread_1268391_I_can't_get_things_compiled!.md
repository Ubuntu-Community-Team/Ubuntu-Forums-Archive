---
title: "I can't get things compiled!"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-16
I'm trying to install something, an Xfce panel plugin (not available in Synaptic, I don't think), and I can't get it to work right even though  the instructions are simple. I type ,/configure, and I get this..  the bottom part of the log is the important part. What can I do to get this to work? Why doesn't it find X? 

> rob@rob-desktop:/tmp/xfce4-modemlights-plugin-0.1.3.99$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
checking for library containing strerror... none required
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for ANSI C header files... (cached) yes
checking net/if.h usability... yes
checking net/if.h presence... yes
checking for net/if.h... yes
checking for X... no
configure: error: X Window system libraries and header files are required


---

### Post by orlox on 2009-09-16
You are missing the development files for X.

I believe installing the xserver-xorg-dev package will fix it.

---

### Post by rob86 on 2009-09-16
Hey I installed the xorg dev package in synaptic (it wasn't installed), and it installed a few other things with it, but it didn't seem to help. I still get the same error.

---

### Post by orlox on 2009-09-16
> **rob86 said:**
> Hey I installed the xorg dev package in synaptic (it wasn't installed), and it installed a few other things with it, but it didn't seem to help. I still get the same error.

There are two packages, "xorg-dev" and "xserver-xorg-dev". i believe the one you need is the second.

---

### Post by mc4man on 2009-09-17
ck. on libx11-dev

---

### Post by rob86 on 2009-09-17
I ended up getting it somehow, it might have been libx11-dev, but to be honest, I saw so many lib's and dev's I can't remember exactly. 

Now it's saying.. 

** The required package gtk+-2.0 was not found on your system.
*** Please install gtk+-2.0 (atleast version 2.6.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.


It seems like I need gtk+-2.0, but I can't find it. I'm looking through the packages and there are a whole bunch of files with gtk keywords, and I can't seem to find one with that exact name..unless i'm missing it.

---

### Post by ~sHyLoCk~ on 2009-09-17
Shouoldn't gtk be installed by default? Can you link us to the plugin you are trying to compile?

---

### Post by doorknob60 on 2009-09-17
> **~sHyLoCk~ said:**
> Shouoldn't gtk be installed by default? Can you link us to the plugin you are trying to compile?

Yeah, but not the development files (-dev packages). The package you're looking for might be libgtk2.0-dev.

---

### Post by ~sHyLoCk~ on 2009-09-17
> **doorknob60 said:**
> Yeah, but not the development files (-dev packages). The package you're looking for might be libgtk2.0-dev.

Yeah but the error says it can't find gtk, and not gtk dev files.

---

### Post by rob86 on 2009-09-17
Well I saw somewhere else on here that it might be the libgtk-dev files, which I don't have installed. I do however have libgtk installed. I guess I'll try libgtk-dev, but it will have to wait until tomorrow, big files..

---

### Post by wobin77 on 2009-09-17
Not 100% sure, but maybe 'xorg-x11-devel' should help....?

---

### Post by mc4man on 2009-09-17
After you install libgtk2.0-dev I'd suspect you'll have several more missing debs to install, probably libxfce* -dev's. Just search them out in your package manager and work you're way thru.

---

