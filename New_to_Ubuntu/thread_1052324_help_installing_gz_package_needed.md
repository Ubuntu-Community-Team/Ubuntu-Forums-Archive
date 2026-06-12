---
title: "help installing gz package needed"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-01-27
When I run

./configure --with-xorg-modules-dir=/usr/lib/xorg/modules/input/

for some tablet drivers I get the message:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

How do I fix that? I'm new to Linux, so I ask many stupid questions.

---

### Post by oldos2er on 2009-01-27
Run
```
sudo apt-get update && sudo apt-get install build-essential
```
in a terminal.

---

### Post by mjheagle8 on 2009-01-27
what specifically are you doing that for?
did you look at the config.log to see what problems there may be?
also, try running the command with sudo.

---

### Post by ivanvajar on 2009-01-27
Thanks!

---

### Post by mjheagle8 on 2009-01-27
no problem, glad to be able to help!

---

