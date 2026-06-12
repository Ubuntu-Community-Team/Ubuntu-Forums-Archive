---
title: "error when installing .tar.bz2"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by prime85 on 2009-08-05
im trying to install the program and i am following the directions from the install document inside. this is the what i am getting..... i dont know how to fix the error.

prime@Prime:/usr/local/src/conky-1.7.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for fopencookie... yes
checking for LUA... no
checking for LUA51... no
checking for LUA51... configure: error: Package requirements (lua5.1 >= 5.1) were not met:

No package 'lua5.1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LUA51_CFLAGS
and LUA51_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.





Someone please help.:confused:

---

### Post by Bigtime_Scrub on 2009-08-05
It sounds like a dependancy problem. If you really want to compile from source thats fine...

As I am not on Ubuntu right now I don't know for sure if that package is in the repositories...

I am on Debian Lenny and it is here when I searched for it in synaptic. So I would suggest you search for it as well, install it with synaptic, then go back and try to do ./configure and see what happens.

---

### Post by SunnyRabbiera on 2009-08-05
what are you trying to install?

---

### Post by oldos2er on 2009-08-05
There are a couple different liblua5.1*dev packages available, not sure which ones your program needs (since you don't say what program it is).

---

### Post by prime85 on 2009-08-05
The program is conky i know there is one in the repository but i was trying to learn how to install from .tar.bz2 files. i installed the lua5.1 files from the repository but its like it still cant find them

---

### Post by prime85 on 2009-08-05
i know its probably simple but i have only been using ubuntu for 3 months

---

### Post by Lampi on 2009-08-05
you might find the missing package using apt build dependencies for conky:
```
sudo apt-get build-dep conky
```
this will only offer the necessary tools to build conky from source

---

### Post by prime85 on 2009-08-05
i guess i will just install it from the repository then :-/

I hope it doesnt do this everytime i try to install a .tar.bz2 file

---

### Post by miezebieze on 2009-08-20
meow! Would you just do, what the people told you?
First I installed only lua5.1 - then, after I came here, I remembered, that for compiling I need the *dev packs. So I installed all lua5.1*dev and liblua5.1*dev packs and it worked! 
But I think you can just do the 

sudo apt-get build-dep conky

Lampi mentioned and all is good. (If not already done.)

---

### Post by Locutus_of_Borg on 2009-08-20
compiling anything in ubuntu is a gigantic pain in the *** since practically every single package has been stripped and divided into several sub-packages. so no, when you install python, you did not actually install Python, you need python-dev, python-lib, python-python, python-etc, python-god-damnit, and so on

it's best to use the repositories or else get the full sources for everything and compile and install all dependencies yourself

---

### Post by wizard10000 on 2009-08-20
The INSTALL readme didn't list dependencies?

---

### Post by xteraco on 2011-11-29
Sorry if this is a zombie thread, I didn't check the date. I came across the same problem when trying to compile and install Conky 1.8.1 in Slackware 13.37.  Here is a step by step of how I got the process to work.

1. get lua 5.1.4
2. extract
3. execute this command inside of the lua directory
make linux install

4. goto conky dir
5. execute these commands inside the conky dir
export LUA51_LIBS=/usr/local/lib/liblua.a
export LUA51_CFLAGS="-Wl,-E -ldl -lreadline -lhistory -lncurses"

6. execute these commands inside the conky dir
make ; make install

After doing that everything goes smooth. I found the LIBS and CFLAGS by looking at the debug text that was generated when I did the "make linux install" for Lua. 

Hope this helps someone someday. :)

---

### Post by oldos2er on 2011-11-29
Closed, necromancy.

---

