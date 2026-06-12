---
title: "[SOLVED] Can't compile programs"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by cdmike2k8 on 2008-12-10
I am trying to compile createtorrent, and when I run ./configure, It tells me I need openssl.  I have this installed, as well as build-essensial.  ```
michael@michael-desktop:~/Desktop/createtorrent-1.1.3$ sudo apt-get install openssl build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-desktop:~/Desktop/createtorrent-1.1.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for SHA1 in -lssl... no
configure: error: error, OpenSSL required

```

---

### Post by iaculallad on 2008-12-10
Try installing the libssl-dev file:

```
sudo apt-get install libssl-dev
```

---

### Post by mc4man on 2008-12-10
You also need -devs when available.

libssl-dev

when you see an error like this
> checking for SHA1 in -lssl... no
stick a lib in front and see if installed, also install the -dev if there is one ( ie. libssl

---

### Post by cdmike2k8 on 2008-12-10
So that allows it to run the configure.  when running make, I get this output: ```
michael@michael-desktop:~/Desktop/createtorrent-1.1.3$ make
make  all-am
make[1]: Entering directory `/home/michael/.local/share/Trash/files/createtorrent-1.1.3'
if gcc -DHAVE_CONFIG_H -I. -I. -I.  -D_FILE_OFFSET_BITS=64   -g -O2 -MT createtorrent-main.o -MD -MP -MF ".deps/createtorrent-main.Tpo" -c -o createtorrent-main.o `test -f 'main.c' || echo './'`main.c; \
	then mv -f ".deps/createtorrent-main.Tpo" ".deps/createtorrent-main.Po"; else rm -f ".deps/createtorrent-main.Tpo"; exit 1; fi
main.c: In function ‘create_announce’:
main.c:125: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
main.c:130: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
main.c: In function ‘write_name’:
main.c:181: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long int’
main.c: In function ‘create_from_file’:
main.c:201: warning: format ‘%lld’ expects type ‘long long int’, but argument 3 has type ‘int’
main.c:210: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
main.c: In function ‘format_path’:
main.c:236: warning: format ‘%i’ expects type ‘int’, but argument 4 has type ‘size_t’
main.c:236: warning: format ‘%i’ expects type ‘int’, but argument 4 has type ‘size_t’
main.c: In function ‘create_from_directory’:
main.c:338: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
main.c:343: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc  -g -O2   -o createtorrent  createtorrent-main.o  -lssl 
make[1]: Leaving directory `/home/michael/.local/share/Trash/files/createtorrent-1.1.3'

```
If I then run sudo make install, it seems to install correctly.  Should I be concerned with all the warnings in the output?  Thanks

---

### Post by iaculallad on 2008-12-10
You can ignore those outputs if the application you had compiled executes properly. Just incorrect data type appropriation.

---

### Post by cdmike2k8 on 2008-12-10
Thanks everyone!

---

### Post by mc4man on 2008-12-10
Generally speaking I don't pay alot of attention to warnings, especailly when the make is thousands of lines, unless there is a problem with the app.

In this case I would.

Why are you building from the trash?

I'd cd to your build folder and try a sudo make uninstall, then shift delete the build folder, empty your trash and start over.

here's how it went here

> doug@doug-desktop:~/createtorrent-1.1.4$ ./configure
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
checking for SHA1 in -lssl... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking openssl/sha.h usability... yes
checking openssl/sha.h presence... yes
checking for openssl/sha.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
doug@doug-desktop:~/createtorrent-1.1.4$ make
make  all-am
make[1]: Entering directory `/home/doug/createtorrent-1.1.4'
gcc -DHAVE_CONFIG_H -I.  -D_FILE_OFFSET_BITS=64   -g -O2 -MT createtorrent-main.o -MD -MP -MF .deps/createtorrent-main.Tpo -c -o createtorrent-main.o `test -f 'main.c' || echo './'`main.c
mv -f .deps/createtorrent-main.Tpo .deps/createtorrent-main.Po
gcc  -g -O2   -o createtorrent createtorrent-main.o  -lssl 
make[1]: Leaving directory `/home/doug/createtorrent-1.1.4'
doug@doug-desktop:~/createtorrent-1.1.4$ 



---

### Post by cdmike2k8 on 2008-12-10
Thanks Doug
I didn't even realize it was going from the trash.  I was in the make folder, not in the trash...Oh well, it seems to work.

---

