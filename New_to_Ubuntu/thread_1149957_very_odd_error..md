---
title: "very odd error."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Insanity01 on 2009-05-05
Ok so i'm using compiz and in the ccsm thing i selected desktop cube
and then skydome, animated.

so i downloaded this atlantis animated skydome, but it doesn't want to insall
i do cd /home/dylan/atlants(tab because of some numbers)

then i use the make command and it says 'error, compiz not found'
even tho i have installed it, as it should come as a regular thing on ubuntu 9.04 O.o

Could someone tell me what to do?

-thanks in advance-

EDIT!!!:

It's solved now, i found out how to in the end, thanks to lloyd_B for putting me on the right way ;)

---

### Post by lloyd_b on 2009-05-05
Generally, when "make" results in an error like that, it's because the system is missing a "-dev" package.

In this case, try installing the "compiz-dev" package ("sudo apt-get install compiz-dev" in a terminal window, or use the package manager of your choice).

If you haven't compiled anything on that machine before, I'd also suggest installing the "build-essential" package.

Lloyd B.

---

### Post by LowSky on 2009-05-05
it in synaptic, install the package called compiz-plugins, it will add a few other things as well, like more animations options for opening closing windows too

dont know if it works, i never use it

---

### Post by Insanity01 on 2009-05-05
the thing lloyd set did get me rid of my old error, but now the error changed into BCOP not installed, and btw i have the plugins ^^

EDIT:

oh i found the BCOP thing, now again something missing 

dylan@ubuntu:~/atlantis$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : float.c -> build/float.lo/bin/sh: libtool: not found
make: *** [build/float.lo] Fout 127

error 127. might find later on ^^

---

### Post by lloyd_b on 2009-05-05
> **Insanity01 said:**
> the thing lloyd set did get me rid of my old error, but now the error changed into BCOP not installed, and btw i have the plugins ^^

EDIT:

oh i found the BCOP thing, now again something missing 

dylan@ubuntu:~/atlantis$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : float.c -> build/float.lo/bin/sh: libtool: not found
make: *** [build/float.lo] Fout 127

error 127. might find later on ^^
Try installing the "libtool" package...

Lloyd B.

---

### Post by Insanity01 on 2009-05-05
> **lloyd_b said:**
> Try installing the "libtool" package...

Lloyd B.

yeah i found out, i said i did lol, edited the first msg from me ^^
i'm not fairly new but not stupid xD

---

