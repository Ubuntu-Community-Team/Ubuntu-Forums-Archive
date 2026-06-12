---
title: "Errors installing iptables-20090111"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-11
These are the installation instructions available in the iptables-20090111 folder.

```
Installation instructions for iptables
======================================

iptables uses the well-known configure(autotools) infrastructure.

	$ ./configure
	$ make
	# make install


```

and here is what I get when I run these commands:

```
looi76@looi76-laptop:~$ cd /home/looi76/Desktop/iptables-20090111/
looi76@looi76-laptop:~/Desktop/iptables-20090111$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes

checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating extensions/GNUmakefile
config.status: creating libipq/Makefile
config.status: creating include/xtables.h
config.status: creating xtables.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
looi76@looi76-laptop:~/Desktop/iptables-20090111$ make
make  all-recursive
make[1]: Entering directory `/home/looi76/Desktop/iptables-20090111'
Making all in extensions
make[2]: Entering directory `/home/looi76/Desktop/iptables-20090111/extensions'
  CC       libxt_CLASSIFY.oo
libxt_CLASSIFY.c:115: fatal error: opening dependency file ./.libxt_CLASSIFY.oo.d: Permission denied
compilation terminated.
make[2]: *** [libxt_CLASSIFY.oo] Error 1
make[2]: Leaving directory `/home/looi76/Desktop/iptables-20090111/extensions'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/looi76/Desktop/iptables-20090111'
make: *** [all] Error 2
looi76@looi76-laptop:~/Desktop/iptables-20090111$ make install
Making install in extensions
make[1]: Entering directory `/home/looi76/Desktop/iptables-20090111/extensions'
  CC       libxt_CLASSIFY.oo
libxt_CLASSIFY.c:115: fatal error: opening dependency file ./.libxt_CLASSIFY.oo.d: Permission denied
compilation terminated.
make[1]: *** [libxt_CLASSIFY.oo] Error 1
make[1]: Leaving directory `/home/looi76/Desktop/iptables-20090111/extensions'
make: *** [install-recursive] Error 1
looi76@looi76-laptop:~/Desktop/iptables-20090111$ 

```

What is going wrong?

---

### Post by adult swim on 2009-01-11
instead of ```
make install
``` use ```
sudo make install
``` assuming your ./configure and make work, this will almost always be the case
EDIT: you can tell this is the case from your instructions ```
$ ./configure
$ make
# make install
```
see how at the end the first character switches from a $ to a #, the # represents being root.  this means you need to use sudo.

---

### Post by jemate18 on 2009-01-11
you need super user privilege when installing / compiling pakage

You can do it by having a "sudo" before the command

$ sudo ./.configure
$ sudo make && make install

---

### Post by looi76 on 2009-01-12
I used **sudo ./.configure** and **sudo make && make install** and still got errors!

```
looi76@looi76-laptop:~$ cd /home/looi76/Desktop/iptables-20090111/
looi76@looi76-laptop:~/Desktop/iptables-20090111$ sudo ./configure
[sudo] password for looi76: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating extensions/GNUmakefile
config.status: creating libipq/Makefile
config.status: creating include/xtables.h
config.status: creating xtables.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
looi76@looi76-laptop:~/Desktop/iptables-20090111$ sudo make && make install
make  all-recursive
make[1]: Entering directory `/home/looi76/Desktop/iptables-20090111'
Making all in extensions
make[2]: Entering directory `/home/looi76/Desktop/iptables-20090111/extensions'
  CC       libxt_CLASSIFY.oo
  CCLD     libxt_CLASSIFY.so
  CC       libxt_comment.oo
  CCLD     libxt_comment.so
  CC       libxt_connbytes.oo
  CCLD     libxt_connbytes.so
  CC       libxt_connlimit.oo
  CCLD     libxt_connlimit.so
  CC       libxt_connmark.oo
  CCLD     libxt_connmark.so
  CC       libxt_CONNMARK.oo
  CCLD     libxt_CONNMARK.so
  CC       libxt_CONNSECMARK.oo
  CCLD     libxt_CONNSECMARK.so
  CC       libxt_conntrack.oo
  CCLD     libxt_conntrack.so
  CC       libxt_dccp.oo
  CCLD     libxt_dccp.so
  CC       libxt_dscp.oo
  CCLD     libxt_dscp.so
  CC       libxt_DSCP.oo
  CCLD     libxt_DSCP.so
  CC       libxt_esp.oo
  CCLD     libxt_esp.so
  CC       libxt_hashlimit.oo
  CCLD     libxt_hashlimit.so
  CC       libxt_helper.oo
  CCLD     libxt_helper.so
  CC       libxt_iprange.oo
  CCLD     libxt_iprange.so
  CC       libxt_length.oo
  CCLD     libxt_length.so
  CC       libxt_limit.oo
  CCLD     libxt_limit.so
  CC       libxt_mac.oo
  CCLD     libxt_mac.so
  CC       libxt_mark.oo
  CCLD     libxt_mark.so
  CC       libxt_MARK.oo
  CCLD     libxt_MARK.so
  CC       libxt_multiport.oo
  CCLD     libxt_multiport.so
  CC       libxt_NFLOG.oo
  CCLD     libxt_NFLOG.so
  CC       libxt_NFQUEUE.oo
  CCLD     libxt_NFQUEUE.so
  CC       libxt_NOTRACK.oo
  CCLD     libxt_NOTRACK.so
  CC       libxt_owner.oo
libxt_owner.c: In function ‘owner_mt_print_item_v0’:
libxt_owner.c:327: warning: format not a string literal and no format arguments
libxt_owner.c: In function ‘owner_mt6_print_item_v0’:
libxt_owner.c:378: warning: format not a string literal and no format arguments
  CCLD     libxt_owner.so
  CC       libxt_physdev.oo
  CCLD     libxt_physdev.so
  CC       libxt_pkttype.oo
  CCLD     libxt_pkttype.so
  CC       libxt_quota.oo
  CCLD     libxt_quota.so
  CC       libxt_rateest.oo
  CCLD     libxt_rateest.so
  CC       libxt_RATEEST.oo
  CCLD     libxt_RATEEST.so
  CC       libxt_recent.oo
  CCLD     libxt_recent.so
  CC       libxt_sctp.oo
  CCLD     libxt_sctp.so
  CC       libxt_SECMARK.oo
  CCLD     libxt_SECMARK.so
  CC       libxt_socket.oo
  CCLD     libxt_socket.so
  CC       libxt_standard.oo
  CCLD     libxt_standard.so
  CC       libxt_state.oo
  CCLD     libxt_state.so
  CC       libxt_statistic.oo
  CCLD     libxt_statistic.so
  CC       libxt_string.oo
  CCLD     libxt_string.so
  CC       libxt_tcp.oo
  CCLD     libxt_tcp.so
  CC       libxt_tcpmss.oo
  CCLD     libxt_tcpmss.so
  CC       libxt_TCPMSS.oo
  CCLD     libxt_TCPMSS.so
  CC       libxt_TCPOPTSTRIP.oo
  CCLD     libxt_TCPOPTSTRIP.so
  CC       libxt_time.oo
  CCLD     libxt_time.so
  CC       libxt_tos.oo
  CCLD     libxt_tos.so
  CC       libxt_TOS.oo
  CCLD     libxt_TOS.so
  CC       libxt_TPROXY.oo
  CCLD     libxt_TPROXY.so
  CC       libxt_TRACE.oo
  CCLD     libxt_TRACE.so
  CC       libxt_u32.oo
  CCLD     libxt_u32.so
  CC       libxt_udp.oo
  CCLD     libxt_udp.so
  CC       libipt_addrtype.oo
In file included from ../include/linux/netfilter_ipv4/ip_tables.h:18,
                 from libipt_addrtype.c:11:
../include/linux/netfilter_ipv4.h:53: error: ‘INT_MIN’ undeclared here (not in a function)
../include/linux/netfilter_ipv4.h:63: error: ‘INT_MAX’ undeclared here (not in a function)
make[2]: *** [libipt_addrtype.oo] Error 1
make[2]: Leaving directory `/home/looi76/Desktop/iptables-20090111/extensions'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/looi76/Desktop/iptables-20090111'
make: *** [all] Error 2
looi76@looi76-laptop:~/Desktop/iptables-20090111$ 

```

---

### Post by adult swim on 2009-01-12
sudo make && make install is like running the two commands

sudo make

make install

you need to only use sudo on make install so run
```
./configure

make

sudo make install
```

---

### Post by looi76 on 2009-01-12
I still got errors :( what is going wrong?

```
looi76@looi76-laptop:~$ cd /home/looi76/Desktop/iptables-20090111/
looi76@looi76-laptop:~/Desktop/iptables-20090111$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating extensions/GNUmakefile
config.status: creating libipq/Makefile
config.status: creating include/xtables.h
config.status: creating xtables.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
looi76@looi76-laptop:~/Desktop/iptables-20090111$ make
make  all-recursive
make[1]: Entering directory `/home/looi76/Desktop/iptables-20090111'
Making all in extensions
make[2]: Entering directory `/home/looi76/Desktop/iptables-20090111/extensions'
  CC       libxt_CLASSIFY.oo
libxt_CLASSIFY.c:115: fatal error: opening dependency file ./.libxt_CLASSIFY.oo.d: Permission denied
compilation terminated.
make[2]: *** [libxt_CLASSIFY.oo] Error 1
make[2]: Leaving directory `/home/looi76/Desktop/iptables-20090111/extensions'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/looi76/Desktop/iptables-20090111'
make: *** [all] Error 2
looi76@looi76-laptop:~/Desktop/iptables-20090111$ sudo make install
[sudo] password for looi76: 
Making install in extensions
make[1]: Entering directory `/home/looi76/Desktop/iptables-20090111/extensions'
  CC       libxt_CLASSIFY.oo
  CCLD     libxt_CLASSIFY.so
  CC       libxt_comment.oo
  CCLD     libxt_comment.so
  CC       libxt_connbytes.oo
  CCLD     libxt_connbytes.so
  CC       libxt_connlimit.oo
  CCLD     libxt_connlimit.so
  CC       libxt_connmark.oo
  CCLD     libxt_connmark.so
  CC       libxt_CONNMARK.oo
  CCLD     libxt_CONNMARK.so
  CC       libxt_CONNSECMARK.oo
  CCLD     libxt_CONNSECMARK.so
  CC       libxt_conntrack.oo
  CCLD     libxt_conntrack.so
  CC       libxt_dccp.oo
  CCLD     libxt_dccp.so
  CC       libxt_dscp.oo
  CCLD     libxt_dscp.so
  CC       libxt_DSCP.oo
  CCLD     libxt_DSCP.so
  CC       libxt_esp.oo
  CCLD     libxt_esp.so
  CC       libxt_hashlimit.oo
  CCLD     libxt_hashlimit.so
  CC       libxt_helper.oo
  CCLD     libxt_helper.so
  CC       libxt_iprange.oo
  CCLD     libxt_iprange.so
  CC       libxt_length.oo
  CCLD     libxt_length.so
  CC       libxt_limit.oo
  CCLD     libxt_limit.so
  CC       libxt_mac.oo
  CCLD     libxt_mac.so
  CC       libxt_mark.oo
  CCLD     libxt_mark.so
  CC       libxt_MARK.oo
  CCLD     libxt_MARK.so
  CC       libxt_multiport.oo
  CCLD     libxt_multiport.so
  CC       libxt_NFLOG.oo
  CCLD     libxt_NFLOG.so
  CC       libxt_NFQUEUE.oo
  CCLD     libxt_NFQUEUE.so
  CC       libxt_NOTRACK.oo
  CCLD     libxt_NOTRACK.so
  CC       libxt_owner.oo
libxt_owner.c: In function ‘owner_mt_print_item_v0’:
libxt_owner.c:327: warning: format not a string literal and no format arguments
libxt_owner.c: In function ‘owner_mt6_print_item_v0’:
libxt_owner.c:378: warning: format not a string literal and no format arguments
  CCLD     libxt_owner.so
  CC       libxt_physdev.oo
  CCLD     libxt_physdev.so
  CC       libxt_pkttype.oo
  CCLD     libxt_pkttype.so
  CC       libxt_quota.oo
  CCLD     libxt_quota.so
  CC       libxt_rateest.oo
  CCLD     libxt_rateest.so
  CC       libxt_RATEEST.oo
  CCLD     libxt_RATEEST.so
  CC       libxt_recent.oo
  CCLD     libxt_recent.so
  CC       libxt_sctp.oo
  CCLD     libxt_sctp.so
  CC       libxt_SECMARK.oo
  CCLD     libxt_SECMARK.so
  CC       libxt_socket.oo
  CCLD     libxt_socket.so
  CC       libxt_standard.oo
  CCLD     libxt_standard.so
  CC       libxt_state.oo
  CCLD     libxt_state.so
  CC       libxt_statistic.oo
  CCLD     libxt_statistic.so
  CC       libxt_string.oo
  CCLD     libxt_string.so
  CC       libxt_tcp.oo
  CCLD     libxt_tcp.so
  CC       libxt_tcpmss.oo
  CCLD     libxt_tcpmss.so
  CC       libxt_TCPMSS.oo
  CCLD     libxt_TCPMSS.so
  CC       libxt_TCPOPTSTRIP.oo
  CCLD     libxt_TCPOPTSTRIP.so
  CC       libxt_time.oo
  CCLD     libxt_time.so
  CC       libxt_tos.oo
  CCLD     libxt_tos.so
  CC       libxt_TOS.oo
  CCLD     libxt_TOS.so
  CC       libxt_TPROXY.oo
  CCLD     libxt_TPROXY.so
  CC       libxt_TRACE.oo
  CCLD     libxt_TRACE.so
  CC       libxt_u32.oo
  CCLD     libxt_u32.so
  CC       libxt_udp.oo
  CCLD     libxt_udp.so
  CC       libipt_addrtype.oo
In file included from ../include/linux/netfilter_ipv4/ip_tables.h:18,
                 from libipt_addrtype.c:11:
../include/linux/netfilter_ipv4.h:53: error: ‘INT_MIN’ undeclared here (not in a function)
../include/linux/netfilter_ipv4.h:63: error: ‘INT_MAX’ undeclared here (not in a function)
make[1]: *** [libipt_addrtype.oo] Error 1
make[1]: Leaving directory `/home/looi76/Desktop/iptables-20090111/extensions'
make: *** [install-recursive] Error 1
looi76@looi76-laptop:~/Desktop/iptables-20090111$ 

```

---

### Post by looi76 on 2009-01-16
It has been 4 days and tell now I can't find a solution! I don't know why I'm getting errors while trying to install iptables! HELP :(

---

