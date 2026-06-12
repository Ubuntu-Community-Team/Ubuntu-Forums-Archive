---
title: "configure gcc question"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by pacalici on 2011-05-12
hello,

my story goes like this:

i removed gcc from synaptic.

i downloaded gcc-3.2.tar.gz (i need this particular version), extracted it to a srcdir and now i'm tryin' to configure it.

when i issue 'srcdir/configure options' i get this:

Configuring for a x86_64-unknown-linux-gnu host.
Created "Makefile" in /home/saba/gcc32/objdir using "mt-frag"
/tmp/cNf31052/cNf31052.pos: 7: cc: not found
*** The command 'cc -o conftest -g   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.

as explained here: [http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html), 'either cc or gcc must be in my path or i must set CC in my environment before running configure'.

1. how can the gcc compiler be in my path if it's not even built?
2. if 1 is the case, how can i set CC appropriately?
3. if anybody answers 2, could they be kind enough to also answer 1? i 'd like to understand what i'm doing.

thanks

pacalici, first quark of ubuntu

---

### Post by pacalici on 2011-05-12
if anybody else gets stuck here, i found the answer to 1 here: [http://forum.osdev.org/viewtopic.php?f=11&t=5080&start=0](http://forum.osdev.org/viewtopic.php?f=11&t=5080&start=0) and i solved 2 just be reinstalling gcc from synaptics.

---

