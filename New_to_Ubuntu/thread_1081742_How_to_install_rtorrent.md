---
title: "How to install rtorrent"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by jonw860 on 2009-02-26
How would I compile the newest version of rtorrent in ubuntu server?

---

### Post by taurus on 2009-02-26
The latest version in the repos is 0.8.2 and the latest stable version from their site is also 0.8.2.  So, do you want version 0.8.2. or the unstable version 0.8.4?

[http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by jonw860 on 2009-02-26
Well I am on a private site that says the way the newest stable version, so how would i compile it and install it?

---

### Post by taurus on 2009-02-26
I assume stable version you mean rtorrent-0.8.2.tar.gz.  Download or save it to somewhere on your $HOME, assuming it's in ~/temp.  Unpack it with

```
cd ~/temp
tar xvzf rtorrent-0.8.2.tar.gz
cd rtorrent-0.8.2
```
And before you build and install it, you need to install the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```
Now, build and install it.

```
./configure
make
sudo make install
```
Of course, you need to make sure you have ncurses already installed on your machine since it will look for that.

---

### Post by jonw860 on 2009-02-26
I got everything but the last part to run it says this.

make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

---

### Post by taurus on 2009-02-26
Did you get an error message when you ran the ./configure command?  Post the whole output of ./configure.

---

### Post by jonw860 on 2009-02-26
No found out why its cause I don't have the ncurses how would I install them?

---

### Post by taurus on 2009-02-26
```
sudo apt-get update
sudo apt-get install ncurses-bin
```

---

### Post by jonw860 on 2009-02-26
Says I already have it this is the error i am getting.

*** The ncurses library is required!
admin@ks357565:~/rtorrent-0.8.2$ make
make: *** No targets specified and no makefile found. Stop.
admin@ks357565:~/rtorrent-0.8.2$ sudo make install
make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

---

### Post by taurus on 2009-02-26
```
sudo apt-get update
sudo apt-get install libncurses5
```

---

### Post by jonw860 on 2009-02-26
Couldn't find libcurses5 is what it says.

---

### Post by taurus on 2009-02-26
> **jonw860 said:**
> Couldn't find lib**[COLOR="Red"]n[/COLOR]**curses5 is what it says.

You forgot an **n** in there.

---

### Post by jonw860 on 2009-02-26
This is what I still get and it says thats already installed

*** The ncurses library is required!
admin@ks357565:~/rtorrent-0.8.2$ make
make: *** No targets specified and no makefile found. Stop.
admin@ks357565:~/rtorrent-0.8.2$ sudo make install
[sudo] password for admin:
make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

---

### Post by taurus on 2009-02-26
Maybe you need the -dev also.

```
apt-get install libncurses5-dev
```

---

### Post by jonw860 on 2009-02-26
Yes that problem is gone but now I get this, also thanks for all the help cause I am sure this is getting on your nerves.

admin@ks357565:~/rtorrent-0.8.2$ make
make: *** No targets specified and no makefile found. Stop.
admin@ks357565:~/rtorrent-0.8.2$ sudo make install
make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

---

### Post by taurus on 2009-02-26
If there is an error with ./configure, no need to run make and sudo make install because they would not work.  What are the last few lines of the output when you run ./configure?

---

### Post by jonw860 on 2009-02-26
Here you go

rtorrent-0.8.2/src/input/path_input.h
rtorrent-0.8.2/src/input/text_input.cc
rtorrent-0.8.2/src/input/text_input.h
rtorrent-0.8.2/src/main.cc
rtorrent-0.8.2/src/Makefile.am
rtorrent-0.8.2/src/Makefile.in
rtorrent-0.8.2/src/option_parser.cc
rtorrent-0.8.2/src/option_parser.h
rtorrent-0.8.2/src/rpc/
rtorrent-0.8.2/src/rpc/command.h
rtorrent-0.8.2/src/rpc/command_map.cc
rtorrent-0.8.2/src/rpc/command_map.h
rtorrent-0.8.2/src/rpc/command_scheduler.cc
rtorrent-0.8.2/src/rpc/command_scheduler.h
rtorrent-0.8.2/src/rpc/command_scheduler_item.cc
rtorrent-0.8.2/src/rpc/command_scheduler_item.h
rtorrent-0.8.2/src/rpc/command_slot.cc
rtorrent-0.8.2/src/rpc/command_slot.h
rtorrent-0.8.2/src/rpc/command_variable.cc
rtorrent-0.8.2/src/rpc/command_variable.h
rtorrent-0.8.2/src/rpc/exec_file.cc
rtorrent-0.8.2/src/rpc/exec_file.h
rtorrent-0.8.2/src/rpc/Makefile.am
rtorrent-0.8.2/src/rpc/Makefile.in
rtorrent-0.8.2/src/rpc/parse.cc
rtorrent-0.8.2/src/rpc/parse.h
rtorrent-0.8.2/src/rpc/parse_commands.cc
rtorrent-0.8.2/src/rpc/parse_commands.h
rtorrent-0.8.2/src/rpc/scgi.cc
rtorrent-0.8.2/src/rpc/scgi.h
rtorrent-0.8.2/src/rpc/scgi_task.cc
rtorrent-0.8.2/src/rpc/scgi_task.h
rtorrent-0.8.2/src/rpc/xmlrpc.cc
rtorrent-0.8.2/src/rpc/xmlrpc.h
rtorrent-0.8.2/src/signal_handler.cc
rtorrent-0.8.2/src/signal_handler.h
rtorrent-0.8.2/src/ui/
rtorrent-0.8.2/src/ui/download.cc
rtorrent-0.8.2/src/ui/download.h
rtorrent-0.8.2/src/ui/download_list.cc
rtorrent-0.8.2/src/ui/download_list.h
rtorrent-0.8.2/src/ui/element_base.h
rtorrent-0.8.2/src/ui/element_chunks_seen.cc
rtorrent-0.8.2/src/ui/element_chunks_seen.h
rtorrent-0.8.2/src/ui/element_download_list.cc
rtorrent-0.8.2/src/ui/element_download_list.h
rtorrent-0.8.2/src/ui/element_file_list.cc
rtorrent-0.8.2/src/ui/element_file_list.h
rtorrent-0.8.2/src/ui/element_log_complete.cc
rtorrent-0.8.2/src/ui/element_log_complete.h
rtorrent-0.8.2/src/ui/element_menu.cc
rtorrent-0.8.2/src/ui/element_menu.h
rtorrent-0.8.2/src/ui/element_peer_list.cc
rtorrent-0.8.2/src/ui/element_peer_list.h
rtorrent-0.8.2/src/ui/element_string_list.cc
rtorrent-0.8.2/src/ui/element_string_list.h
rtorrent-0.8.2/src/ui/element_text.cc
rtorrent-0.8.2/src/ui/element_text.h
rtorrent-0.8.2/src/ui/element_tracker_list.cc
rtorrent-0.8.2/src/ui/element_tracker_list.h
rtorrent-0.8.2/src/ui/element_transfer_list.cc
rtorrent-0.8.2/src/ui/element_transfer_list.h
rtorrent-0.8.2/src/ui/Makefile.am
rtorrent-0.8.2/src/ui/Makefile.in
rtorrent-0.8.2/src/ui/root.cc
rtorrent-0.8.2/src/ui/root.h
rtorrent-0.8.2/src/utils/
rtorrent-0.8.2/src/utils/directory.cc
rtorrent-0.8.2/src/utils/directory.h
rtorrent-0.8.2/src/utils/file_status_cache.cc
rtorrent-0.8.2/src/utils/file_status_cache.h
rtorrent-0.8.2/src/utils/list_focus.h
rtorrent-0.8.2/src/utils/lockfile.cc
rtorrent-0.8.2/src/utils/lockfile.h
rtorrent-0.8.2/src/utils/Makefile.am
rtorrent-0.8.2/src/utils/Makefile.in
rtorrent-0.8.2/src/utils/socket_fd.cc
rtorrent-0.8.2/src/utils/socket_fd.h
rtorrent-0.8.2/TODO
admin@ks357565:~$ cd rtorrent-0.8.2
admin@ks357565:~/rtorrent-0.8.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for user-defined CXXFLAGS... user-defined "-g -O2"
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for execinfo.h... no
checking for proper overloaded template function disambiguation... yes
checking for library containing add_wch... no
checking for library containing wbkgdset... -lncurses
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking for statvfs... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for STUFF... configure: error: Package requirements (sigc++-2.0 libcurl >= 7.12.0 libtorrent >= 0.12.2) were not met:

No package 'sigc++-2.0' found
No package 'libcurl' found
No package 'libtorrent' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables STUFF_CFLAGS
and STUFF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

admin@ks357565:~/rtorrent-0.8.2$ make
make: *** No targets specified and no makefile found. Stop.
admin@ks357565:~/rtorrent-0.8.2$ sudo make install
make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

---

### Post by taurus on 2009-02-26
> **jonw860 said:**
> 
checking for STUFF... configure: error: Package requirements (sigc++-2.0 libcurl >= 7.12.0 libtorrent >= 0.12.2) were not met:

No package '**[COLOR="Red"]sigc++-2.0[/COLOR]**' found
No package '**[COLOR="Red"]libcurl[/COLOR]**' found
No package '**[COLOR="Red"]libtorrent[/COLOR]**' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables STUFF_CFLAGS
and STUFF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

You need to go back to the link that I included in my previous message to download the libtorrent and build that first.  You also need to install sigc++ & libcurl from the repos.  Then, run the ./configure in ~/rtorrent-0.8.2 again.

```
sudo apt-get install libsigcperl-dev libcurl4-openssl-dev
```
 
> admin@ks357565:~/rtorrent-0.8.2$ **make**
make: *** No targets specified and no makefile found. Stop.
admin@ks357565:~/rtorrent-0.8.2$ **sudo make install**
make: *** No rule to make target `install'. Stop.
admin@ks357565:~/rtorrent-0.8.2$

Please do not run these two commands until ./configure returns with a success.  Otherwise, it's just a waste of time.

Again, any reason why you don't want to install rtorrent from the repos since it's a 0.8.2 version which you are trying to compile right now?

---

### Post by jonw860 on 2009-02-26
Could you please break this down step by step I am super confused sorry I am a noob.

---

### Post by taurus on 2009-02-26
Here is something a little less confuse.  Type these two commands in a terminal (one at a time) and post the outputs of them.

```
sudo apt-get update
sudo apt-get install rtorrent
```

---

### Post by jonw860 on 2009-02-26
Can't find sigc++ & libcurl, also this is for my seedbox a site I am on won't let me use the older version in the repositories.

---

### Post by dudko on 2009-12-13
> **taurus said:**
> Here is something a little less confuse.  Type these two commands in a terminal (one at a time) and post the outputs of them.

```
sudo apt-get update
sudo apt-get install rtorrent
```


Pls, taurus, are there any differecies between installation

apt-get install rtorrent 

and installation step by step?

---

### Post by Troll_the_Great on 2009-12-13
> **dudko said:**
> Pls, taurus, are there any differecies between installation

apt-get install rtorrent 

and installation step by step?

That installation "step by step" as you called it is compiling from source and "sudo apt-get install rtorrent" is a direct install from a .deb file from the repositories.
I think you are familiar with windows. A .deb file is equivalent (in a way) with a .exe file from windows: you just double click on it, type your password and the program install itself (so, in another words, the file is **already prepared** for your operating system).
A source file (.tar.gz, .tgz and so on) has no equivalent in the windows world. It's a raw information with has to be compiled for your operating system in order to work. Source file exists because not every software manufacturer has time compile a program for every major branch of Linux distributions (for example, Ubuntu uses .deb, Mandriva uses .rpm. Gentoo uses source code, and so on). So it's easier to just release the source code and every user compiles it for his own distribution. Windows has so source files because it's a close source operating system, so nobody (except his developers) can see his "recipe". This goes for the programs too, because the majority of programs for windows are close source also. 
To give you an example, is like buying a new suit. You can either go to the store and choose one from a list of suits the one that is good for you (a .deb file), or you can buy a piece of cloth and make your own suit (a source file).
I hope you understand what I mean. If not, post back any questions you have and I will try to help you.
Cheers!

---

