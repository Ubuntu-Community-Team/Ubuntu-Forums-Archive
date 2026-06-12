---
title: "Linux Hyperterminal?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by ryanwithrow on 2009-02-09
I have just switched to Linux, Ubuntu 8.10, and so far I am very happy. I need to find a program similar to Hyper Terminal, because I configure Cisco routers regularly. Any advice would be appreciated.

---

### Post by drs305 on 2009-02-09
Whenever I wonder what linux app I can substitute, I first visit this site ([_http://www.linuxalt.com/_]("http://www.linuxalt.com/")). I found two entries: *minicom* and *GtkTerm*. You could search for information on these two apps and perhaps users can provide some feedback on them.

---

### Post by ryanwithrow on 2009-02-09
Thanks, that is a great site, I will check those out!

---

### Post by ryanwithrow on 2009-02-09
I tried to install both, and am confused. Neither has a Deb install, and I have never done a Source install before. I followed the directions in minicom, doing the ./configure, make, then make install, but then it wants me to configure the serial connections, which I do not know how to do, and I am unable to locate a graphical UI for the application. GTKTERM doesn't have any directions in the read me files, I tried doing a ./configure, that worked, but make failed. Can anyone give advice to a Linux beginner?

Thanks in advance

---

### Post by PirateChef on 2009-02-09
> **ryanwithrow said:**
>  GTKTERM doesn't have any directions in the read me files, I tried doing a ./configure, that worked, but make failed. Can anyone give advice to a Linux beginner?

Thanks in advance

What error(s) did you get from make?

---

### Post by ryanwithrow on 2009-02-09
root@ryan-laptop:/home/ryan/Downloads/gtkterm-0.99.5# ./configure
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking POSIX termios... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether we are using the GNU C Library 2 or newer... yes
checking for ranlib... ranlib
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for TERMINAL_WIDGET... configure: error: Package requirements (vte >= 0.10.4) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the TERMINAL_WIDGET_CFLAGS and TERMINAL_WIDGET_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
root@ryan-laptop:/home/ryan/Downloads/gtkterm-0.99.5# make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by Sorivenul on 2009-02-09
gtkterm and minicom are both in the repositories:

```
sudo apt-get install gtkterm
```

or 

```
sudo apt-get install minicom
```

Good luck!

---

### Post by Malalo on 2009-02-09
I manage Cisco switches and can connect to them by Telnet, using xterm (basic terminal in Ubuntu), just by typing 

```
telnet *ip_address_of_switch*
```

---

### Post by ryanwithrow on 2009-02-09
Yeah, but I need to configure brand new devices who don't have an IP yet. I got GTKTERM installed through apt-get install, now to figure out how to configure it :D Thanks everyone for the help.

---

### Post by Malalo on 2009-02-09
Oh ok... So then I guess you're connecting through the CONSOLE port... then GTKTERM is a proper tool.
Good luck !

---

### Post by Sorivenul on 2009-02-09
> **ryanwithrow said:**
> Yeah, but I need to configure brand new devices who don't have an IP yet. I got GTKTERM installed through apt-get install, now to figure out how to configure it :D Thanks everyone for the help.
Open it up, and a default configuration will be created in your home folder. Then just edit it with your editor of choice, e.g.:
```
nano /home/yourusername/.gtktermrc
```

---

### Post by jcl43 on 2009-02-09
gkterm is good, i use putty which is free telnet/ssh client. it also has terminal functionality. works great on any platform

[http://linux.softpedia.com/get/System/Networking/PuTTY-347.shtml](http://linux.softpedia.com/get/System/Networking/PuTTY-347.shtml)

---

### Post by Fire_Chief on 2009-02-09
I've been working with equipment like this for years and the best app I've found to handle console connections is actually PuTTY. Most people know it only for Telnet/SSH connections but it does perfectly well for console connections too.

and it is available from the repos. :)

Cheers!

---

### Post by ryanwithrow on 2009-02-10
> **Fire_Chief said:**
> I've been working with equipment like this for years and the best app I've found to handle console connections is actually PuTTY. Most people know it only for Telnet/SSH connections but it does perfectly well for console connections too.

and it is available from the repos. :)

Cheers!

Thanks for the Help. Putty is a perfect solution, as I already have it, and I am already familiar with the interface. I had no idea it could do Serial connections for all this time :D

Thanks everyone for the help

---

