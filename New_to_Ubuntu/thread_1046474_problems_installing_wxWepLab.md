---
title: "problems installing wxWepLab"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by etusha on 2009-01-21
im have simalr problem wxweplab 0.1.6
i have install build-essential libpcap

```

weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
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
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
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
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
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
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
root@ervis-laptop:/home/ervis/Desktop/as/weplab# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
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
checking pcap.h usability... yes
checking pcap.h presence... yes
checking for pcap.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for ANSI C header files... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pcap_open_live in -lpcap... yes
warning: compiler is not known: not optimizing!
using gcc -g -O2 -Wall -pipe
configure: creating ./config.status
config.status: creating Makefile
```

```

/weplab# make
make: Nothing to be done for `all'.
```

---

### Post by opscure on 2009-01-21
sudo apt-get install weplab

it's in the repositories and you don't have to build from source that way.

---

### Post by etusha on 2009-01-21
i have install weplab but i need wxweblab

---

### Post by opscure on 2009-01-26
Sorry, it looked like you were trying to make weplab.  Anyway, if you follow the install file you will be able to get wxweplab running by doing:
```
wxWepLab Instalacion notes:
---------------------------

wxWepLab needs weplab-0.1.6 to be compiled in a directory called "weplab".

To do this, just follow these steps:

  1) Create a symbolic link to weplab sources:

  ln -s weplab-0.1.6 weplab

  2) Compile weplab-0.1.6 normaly (libpcap-0.8 needed):

  cd weplab-0.1.6
  ./configure
  make
  make install
  cd ..

  3) Compile wxWepLab (wxWidgets 2.6.x support needed):

  make

  4) Try if it works:

  ./wxweplab

```

Even if the make install reports nothing to be done, it is likely that your version of weplab is up to date.  you can check this further by going into the weplab source directory and doing a:
```
make weplab weplab.1
```

If you want to see the process that make is going through just cat out your Makefile in the respective directories and following the path of the script by the arguments you call to it.  

For example, if you did a make install on a make file in the weplab source directory you would look for the install: call inside the Makefile.  From there you can see what make is doing.

---

### Post by dazzler on 2009-05-06
Did you manage to get this going im in a similar boat.

```
dazzler@dazzler-laptop:~/Desktop/wxweplab-0.1.6-3$ ./wxweplab 
./wxweplab: error while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory

```

wxlab is installed fine

---

