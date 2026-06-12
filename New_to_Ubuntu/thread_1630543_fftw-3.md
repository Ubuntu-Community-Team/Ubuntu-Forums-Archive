---
title: "fftw-3"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by kazhugan on 2010-11-25
Hi,
   Its my first date with linux. Im using ubuntu in a i686 architecture. Was trying to install fftw-3 and im stuck. 
-----------------------------
checking for a BSD- compatible install.../usr/bin/install -c
checking whether build environment is sane...yes
checking for gawk...gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works ... configure: error:cannot run C compiled programs
if you meant to cross compile, use '--host'.
--------------------------

Need help!!
Thanx :)

---

### Post by Daveth on 2010-11-25
might it not be easier to run it as a deb file instead????

[HTML]http://packages.debian.org/search?keywords=fftw3[/HTML]

You might have a few dependency issues to solve, and you need to check your architecture and the exact package.

---

### Post by The Cog on 2010-11-25
Is there any reason you don't want to install the fftw libraries from the repositories? Run System->Administration->Synaptic and search for fftw. For some reason, libfftw3-3 is already installed on my system. I don't know if it's there by default or because something else I installed needs it. There are several fftw packages in synaptic, including documentation.

---

### Post by wannabegeek on 2010-12-08
Hi I'm also trying to install FFTW on a Ubuntu 9.10 machine.
I just joined a research team and have no prior experience with FTTW.

Can I install from repo..?
Do I get fftw2 ?

UPDATE: I installed fftw2, tried man fftw2...nothing...installed fftw-doc...still man does nothing...

TIA
wbg

---

### Post by wannabegeek on 2010-12-08
I guess I posted too soon...

Installed fftw3-dev from repo, found test program in C and compiled it fine...

cheers
wbg

---

