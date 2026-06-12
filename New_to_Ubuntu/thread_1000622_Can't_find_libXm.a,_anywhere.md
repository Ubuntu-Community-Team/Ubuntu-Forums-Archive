---
title: "Can't find libXm.a, anywhere"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by tanksnr on 2008-12-03
Hi all,

New user here, and relatively new to linux.

I'm working with Ubuntu Hardy, and trying to compile something that requires the X11 dev libraries/headers. 

I have installed the neccessary packages (hopefully):
[COLOR="Red"]libpthread-stubs0-dev_0.1-2_i386.deb
libpthread-stubs0_0.1-2_i386.deb
libx11-dev_1.1.3-1ubuntu2_i386.deb
libxau-dev_1.0.3-2_i386.deb
libxcb-xlib0-dev_1.1-1ubuntu1_i386.deb
libxcb1-dev_1.1-1ubuntu1_i386.deb
libxcb1_1.1-1ubuntu1_i386.deb
libxdmcp-dev_1.0.2-2_i386.deb
x11-common_7.3+10ubuntu10_i386.deb
x11proto-core-dev_7.0.11-1_all.deb
x11proto-input-dev_1.4.2-1_all.deb
x11proto-kb-dev_1.0.3-2ubuntu1_all.deb
xtrans-dev_1.0.4-1_all.deb[/COLOR]

Upon compiling I get "/usr/bin/ld: cannot find -lXm".
The makefile is pointing to /usr/X11R6/lib, which is fine.
Though there is no libXm.a in that location.
There is however the various libXm.so* files. 
The same applies to libXt.a, which the compiler (gcc) will look for next.
I do however have the libX11.a.

So, my question is, what am I missing?
What don't I understand about the *.a files?
From what I can see, the gcc flag "-lXm -lXt -lX11 -L/usr/X11R6/lib" 
tells gcc to look for libXm.a, libXt.a and libX11.a in the given location. 
Why is it that after installing the X11 dev packages, do I have the libX11.a (and a few others incl. libXmcp.a) and not libXm.a and libXt.a?

Sorry, its alot of text, but I feel if I explain in detail it'd make things easier. 

Mr Red.

ps, i have posted this on another forum ( [http://www.linuxforums.org/forum/ubuntu-help/135052-cant-find-libxm-anywhere.html#post644428]("http://www.linuxforums.org/forum/ubuntu-help/135052-cant-find-libxm-anywhere.html#post644428") ),though not much happened.

---

### Post by Michael.Godawski on 2008-12-03
> I'm working with Ubuntu Hardy, and trying to compile something that requires the X11 dev libraries/headers.What are you trying to compile? Do you have to compile it? Can't you just install it via Synaptic Package Manager or search for a deb file?

Edit:
ok read the linuxforum thread...

---

### Post by Michael.Godawski on 2008-12-03
Here I found a manual:
[http://www.ie.unc.edu/cempd/EDSS/pave_doc/index.shtml](http://www.ie.unc.edu/cempd/EDSS/pave_doc/index.shtml)

And the installation is made by a script; I do not see anything to compile:
> **2. Installation instructions	**

 To install Version 2.3 of PAVE, expand the tar or zip file into a directory, then type "pave" to run the PAVE script within that directory. If you put the directory containing the PAVE script in your path, the program will run if you type "pave" from any location on your system. On Linux systems, if PAVE doesn't run by just typing "pave" try "sh pave". 

---

### Post by tanksnr on 2008-12-03
Hi Michael,

Thanks for your reply.

It seems the manual assumes you have pave installed, since the step you've mentioned will only work if you have a valid executable (which the script calls). So to get an executable, one would have to compile it.

At the moment, CMAS ([http://www.cmascenter.org/]("http://www.cmascenter.org/")) provide binaries only for RedHat linux. For others, one would have to compile the source. 
Sorry i'd attach the source here but it's like 2mb. Here's the link, [http://paved.sourceforge.net/]("http://paved.sourceforge.net/")

Though I don't think the problem is with pave, since it is not involved in creating the libraries it needs (i.e. the X11 related stuff).

---

### Post by redseventyseven on 2008-12-03
> At the moment, CMAS ([http://www.cmascenter.org/](http://www.cmascenter.org/)) provide binaries only for RedHat linux. For others, one would have to compile the source. 

Have you tried using Alien? It's a tool that converts RPM packages into .deb files. Just an idea...

Alien is available from the Synaptic Package Manager.

---

### Post by Michael.Godawski on 2008-12-03
wow...

I just downloaded this package
[GZipped tar of PAVE 2.3 source code including associated utilities)]("http://paved.sourceforge.net/pave_2.3_src_utils.tar.gz")
navigated into the pave directory and executed sudo make.
What followed was an infinite line of ```
pave/ansdfa/pavaenkanka/gibberish crup 
```
which flooded my system and forced me to restart.

This becomes interesting...

---

### Post by tanksnr on 2008-12-04
redseventyseven: yes i just might give that a go. 

Michael: Sorry for unleashing that on you:). Though you must read the readme before trying to run make. A few environmental variables have to be set. 
As an aside, i'd like to know if you do manage to set those variables in ubuntu, for bash or csh.

---

