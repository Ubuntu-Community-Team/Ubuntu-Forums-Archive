---
title: "error configuring abgx360 1.0.5"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by BritonL on 2011-09-07
Hello, I am having a problem when trying to install abgx360 1.0.5.  I am running Ubuntu 11.04.  When I run ./configure && make, i get this output

> briton@briton-BT437AA-ABA-s5623w:~/abgx360-1.0.5$ ./configure && make
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for crc32 in -lz... yes
checking for gawk... (cached) mawk
checking for curl-config... no
checking whether libcurl is usable... no
configure: error: "libcurl not found!"
I am sure I have libcurl installed, because i just reinstalled it.

btw, I am a total noob to Ubuntu.

---

### Post by Toz on 2011-09-15
Hello and welcome to the forums.

> I am sure I have libcurl installed, because i just reinstalled it.
Which libcurl package did you install?

From the readme file:
> abgx360 requires libcurl ([http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)) and zlib ([http://ww](http://ww)
w.zlib.net/)

To install them on systems with apt-get:
sudo apt-get install libcurl4-openssl-dev zlib1g-dev


Did you install **libcurl4-openssl-dev** and **zlib1g-dev**?

---

