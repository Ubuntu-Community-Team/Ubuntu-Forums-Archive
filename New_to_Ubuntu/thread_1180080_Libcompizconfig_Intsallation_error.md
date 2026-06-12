---
title: "Libcompizconfig Intsallation error"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by sparky8251 on 2009-06-06
Hi I'm new to ubuntu and have had trouble doing even the most simple of tasks like installing gettext so I can install the libcompizconfig so i can install ccsm. I have installed intltools and supposedly gettext but when I run the configure file for libcompizconfig I get the follow text in terminal:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for intltool >= 0.35.0... 0.35.5 found
checking for intltool-update... /usr/local/bin/intltool-update
checking for intltool-merge... /usr/local/bin/intltool-merge
checking for intltool-extract... /usr/local/bin/intltool-extract
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool

So I don't know what to do. Could anyone help me. And before you sugest the "sudo apt-get" command the computer is not connected to the internet. I have been getting files from school.

---

### Post by RedSocrates on 2009-06-06
Out of curiosity, why are you trying to compile these things from source rather than simply installing the .deb files?  You can use 'sudo aptitude download <package_name>' on the computer you've been using at school to simply download the .deb files that apt-get would typically install, then write those .deb files to a disk and install them on your non-connected computer (using 'sudo dpkg -i <deb_file_name>' for each .deb file).  This would essentially be the same as using 'sudo apt-get', except that you'd be able to do it without an internet connection on the non-connected computer.

Another alternative is downloading the required .deb files manually from [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

