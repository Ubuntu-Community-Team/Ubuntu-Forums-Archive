---
title: "How do i install genecys?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by waxyfresh on 2009-02-12
I downloaded the tar.gz but cant figure out how to install it.

Thanks!

---

### Post by snova on 2009-02-12
This looks a bit old... the last download on SF.net is from 2004; last update on their site is early 2005.

Unpack it (it's an archive, probably containing source code) and show me a listing of files inside it.

Oh, and where did you download it to? Your Desktop? Home directory?

Also, it should contain a README file, or hopefully an INSTALL, with instructions.

---

### Post by waxyfresh on 2009-02-12
david@IceWeasel:~/Desktop/a$ dir
arch  etc  libdata  map  textures  var
david@IceWeasel:~/Desktop/a$


this is what was in it,i downlaoded it to /tmp/ and unpacked it.

Heres the original file:

[http://heanet.dl.sourceforge.net/sourceforge/genecys/genecys-data-0.2.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/genecys/genecys-data-0.2.tar.gz)

---

### Post by snova on 2009-02-12
This is the data package; there is another one that contains the program itself.

Hopefully it will also contain some instructions, because this tarball is rather inscrutable...

---

### Post by boywander on 2009-02-12
Something wrong with dgen, gens, generator?
Not sure but I believe they're all more up to date and in the repos.

---

### Post by waxyfresh on 2009-02-13
ok so im up to this point:
> david@IceWeasel:~$ cd a
david@IceWeasel:~/a$ ./configure
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
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
configure: configuring in freesolid
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
configure: error: /bin/bash './configure' failed for freesolid


---

