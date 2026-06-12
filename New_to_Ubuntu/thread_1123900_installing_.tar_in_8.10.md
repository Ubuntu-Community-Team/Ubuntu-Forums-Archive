---
title: "installing .tar in 8.10"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by ubigT on 2009-04-12
trying to install a .tar for a system monitor. Following the instructions in the install file and I get an error that I am missing some packages:

trevor@trevor-desktop:~/Desktop/Hardware Monitor 1.4/hardware-monitor-1.4.1$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/trevor/Desktop/Hardware: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gconfmm-2.6 >= 2.6.0                         gtkmm-2.4 >= 2.6.0                         libgnomecanvasmm-2.6 >= 2.6.0 			libglademm-2.4 >= 2.4.0 		libpanelapplet-2.0 >= 2.0.0                         libgtop-2.0 >= 2.6.0) were not met:

No package 'gconfmm-2.6' found
No package 'gtkmm-2.4' found
No package 'libgnomecanvasmm-2.6' found
No package 'libglademm-2.4' found
No package 'libpanelapplet-2.0' found
No package 'libgtop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have never installed a .tar before so i need some help.... what do I do?

---

### Post by Thedjatclubrock on 2009-04-12
You need to find those packages, and install them using apt or install them from source. They will normally end in -dev in the repos.

> **ubigT said:**
> trying to install a .tar for a system monitor. Following the instructions in the install file and I get an error that I am missing some packages:

trevor@trevor-desktop:~/Desktop/Hardware Monitor 1.4/hardware-monitor-1.4.1$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/trevor/Desktop/Hardware: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gconfmm-2.6 >= 2.6.0                         gtkmm-2.4 >= 2.6.0                         libgnomecanvasmm-2.6 >= 2.6.0 			libglademm-2.4 >= 2.4.0 		libpanelapplet-2.0 >= 2.0.0                         libgtop-2.0 >= 2.6.0) were not met:

No package 'gconfmm-2.6' found
No package 'gtkmm-2.4' found
No package 'libgnomecanvasmm-2.6' found
No package 'libglademm-2.4' found
No package 'libpanelapplet-2.0' found
No package 'libgtop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have never installed a .tar before so i need some help.... what do I do?

---

### Post by llamabr on 2009-04-12
Please don't repost old threads.  Instead, check the old one, where you'll find that others have already posted helpful replies.

---

