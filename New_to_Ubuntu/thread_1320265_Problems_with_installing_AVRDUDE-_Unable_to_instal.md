---
title: "Problems with installing AVRDUDE- Unable to install M4 for flex to detect it"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by lolboy on 2009-11-09
Hi guys,

I am trying to install AVRDUDE. (avrdude-5.5.tar.gz). 

> 
root@computer:/home/lolboy/Desktop/avrdude-5.5# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for ranlib... ranlib
checking for tputs in -ltermcap... no
checking for tputs in -lncurses... no
checking for readline in -lreadline... no
checking for usb_get_string_simple in -lusb... no
checking how to run the C preprocessor... gcc -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for ddk/hidsdi.h... no
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for memset... yes
checking for select... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strtol... yes
checking for strtoul... yes
checking for gettimeofday... yes
checking for a Win32 HID libray... no
checking for parallel device... /dev/parport0
checking for serial device... /dev/ttyS0
configure: creating ./config.status
config.status: creating doc/Makefile
config.status: creating windows/Makefile
config.status: creating avrdude.spec
config.status: creating Makefile
config.status: creating avrdude.conf.tmp
config.status: creating ac_cfg.h
config.status: ac_cfg.h is unchanged
config.status: executing depfiles commands

Which in turn, I went to type:
make: *** [all] Error 2
[/quote]I found on this [particular thread]("http://www.avrfreaks.net/index.php?name=PNphpBB2&file=printview&t=75876&start=0") that the problem was I needed to install flex and which in turn I needed m4. I used (m4-1.4.9.tar.gz). Upon installing, FLEX 

gave this message when configuring:
> configure: error: GNU M4 1.4 is requireddespite repeated installations.

Can someone enlighten me on the installation of GNU m4.1.4 so that FLEX can be configured and MAKEd successfully?

Thanks in advance:)

---

### Post by Kelvin Gardiner on 2009-11-10
Avrdude is in the Ubuntu universe repository see here for how to enable this.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Once the universe repository is enabled, avrdude can be installed using synaptic.

Karmic has avrdude 5.8.

---

