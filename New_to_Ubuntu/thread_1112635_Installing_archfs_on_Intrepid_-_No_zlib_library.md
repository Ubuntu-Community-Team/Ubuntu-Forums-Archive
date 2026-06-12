---
title: "Installing archfs on Intrepid - No zlib library"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by chguerreiro on 2009-03-31
Hello! 

I'm trying to install archfs ([http://code.google.com/p/archfs/]("http://code.google.com/p/archfs/")) on Intrepid. I downloaded the package and extracted it to my home directory.

When running "**./configure**" as instructed by the readme file, I get a message saying "No zlib library!". Complete output:

> user@computer:~/archfs-0.5.4$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ranlib... ranlib
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
checking for gzgets in -lz... no
configure: error: No zlib library!


I checked Synaptic and there are several zlib-related packages, some installed, some not.

Any suggestions on how to solve this? I fell I'm missing something simple.

Thanks!
Fabio

---

### Post by adult swim on 2009-03-31
try ```
sudo apt-get install zlib1g-dev
``` and then cd back to the archfs directory and try to ./configure again

---

### Post by chguerreiro on 2009-03-31
Thanks! It worked perfectly. It then gave me a message it was missing fuse...but I know the "-dev" files are used on those situations, I was able to solve the fuse error myself.

Now I have a problem on 'make' but I will try to understand it better before posting something. ;)

---

### Post by adult swim on 2009-04-02
im glad you figured out the fuse error!  no matter what i did, i was unable to successfully get make to work.

---

### Post by isync on 2010-05-21
When I built archfs, I had an issue with a "missing FUSE", which  [this blog post]("http://linux.goeszen.com/installing-archfs-on-ubuntu-to-browse-rdiff-backup-repositories.html") helped me fix. Also has handy command line help on how to mount and unmount (!) - the latter the archfs manual seems to assume commonly known. ;)

Just my 2c.

---

