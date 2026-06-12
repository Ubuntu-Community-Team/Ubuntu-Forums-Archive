---
title: "help me to solve my problem!plz"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by ubugross on 2008-12-11
Hi, i was just trying to see if all work fine with my new ubuntu intrepid ibex,then i've compiled GNUCHESS 5.06, but something went wrong.
This is the output of the "Configure"
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD compatible install... /usr/bin/install -c
checking for mawk... (cached) mawk
checking whether ln -s works... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tputs in -lncurses... no
checking for readline in -lreadline... no
checking how to run the C preprocessor... gcc -E
checking for readline/readline.h... no
checking for readline/history.h... no
THEN FOLLOWS MANY "YES",BUT FURTHER
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
If i give "make" after "configure", "make" find bugs in the source file like these  error: static declaration of ‘input_thread’ follows non-static declaration
common.h:725: error: previous declaration of ‘input_thread’ was here

many reguards.

---

### Post by Paqman on 2008-12-11
The version of Gnuchess in the repos is 5.07. Is there any particular reason you wanted to compile an older version?

---

### Post by Nepherte on 2008-12-11
Any reason why you are not using gnuchess from the ubuntu repositories?
```
sudo apt-get install gnuchess
```

---

### Post by ubugross on 2008-12-11
> **Paqman said:**
> The version of Gnuchess in the repos is 5.07. Is there any particular reason you wanted to compile an older version?

Thanks for this first quick message!so, repos 5.07 makes the same problems! 
I think that the older version is not the source of my problem...

---

### Post by Michael.Godawski on 2008-12-11
Always search the repositories first:
Add/Remove
Synaptic
then try to find a deb
then ask on the forums
then try to compile.

[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)

---

### Post by ubugross on 2008-12-11
> **Nepherte said:**
> Any reason why you are not using gnuchess from the ubuntu repositories?
```
sudo apt-get install gnuchess
```
You are right,i can play chess and i've just installed in the way that you told me, but i want to study source codes and is my interest to create the program from the source!

---

### Post by ubugross on 2008-12-11
> **Michael.Godawski said:**
> Always search the repositories first:
Add/Remove
Synaptic
then try to find a deb
then ask on the forums
then try to compile.

[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)

hi!what does "to find a deb" mean?

---

### Post by decoherence on 2008-12-11
> **ubugross said:**
> i want to study source codes and is my interest to create the program from the source!

Have you installed the package build-essential? It contains the software needed for compiling source. 

```

sudo apt-get install build-essential
```

try to compile again once you have that installed.

> hi!what does "to find a deb" mean?

"deb" is the package format for Ubuntu and Debian software. All the programs in the repositories are debs. "Find a deb" probably means try to find one on the internet, outside of the official repositories. For instance, [www.getdeb.net](www.getdeb.net)

---

### Post by albinootje on 2008-12-11
> THEN FOLLOWS MANY "YES",BUT FURTHER
> checking for the pthreads library -lpthreads... no
> checking whether pthreads work without any flags... no
> checking whether pthreads work with -Kthread... no

This is probably harmless.

> If i give "make" after "configure", "make" find bugs in the source file
> like these error: static declaration of ‘input_thread’ follows
> non-static declaration
> common.h:725: error: previous declaration of ‘input_thread’ was here

You wrote that you want to study source code.
But in that cause you should use either :

1) the original source code and read the install instructions thoroughly.
or 
2) stick to the ubuntu source packages to make it compile properly

In the latter case you need the deb-src lines enables in your /etc/apt/sources.list

And then it's a matter of :

sudo apt-get build-dep gnuchess

sudo apt-get -b source gnuchess

to make it compile.

In some cases source code needs to be compiled with an earlier version of gcc or some patches are needed to make it compile correctly on a certain Ubuntu release.

With the setup described in 2) you can still look at the source code because the original source code will be downloaded, and then it is being 
compiled.

---

### Post by Kellemora on 2008-12-11
Hi Ubugross

Find a deb means find a downloadable file ALREADY compiled for Debian based Linux.

It means the install file will end in .deb and usually has all the dependencies associated with it, so one install makes it all work.

For example:  you may find files out there that end in .rpm also, those files are compiled for Red Hat Linux and cannot be used on Debian based Linux without recompiling them for same.  There is a program to do so, I think it's name is Alien, but they don't always work.

I know nothing (as Schultz would say!) about compiling or the differences between .rpm and .deb files, other than a Ford Transmission won't bolt up to a Chevy Bell Housing or vice versa.

That being said, back in the olde days, I could get Basic programs written for PC's to work on Apples by changing only a few lines of code that were proprietary to the different systems.
But not always, sometimes those programmers did tricks well beyond my skill level, which has only gone downhill ever since.

Good Luck

TTUL
Gary

---

### Post by ubugross on 2008-12-11
Yes J have the package, but there are the same problems.

---

### Post by oldos2er on 2008-12-11
"checking for the pthreads library -lpthreads... no"

 Looks like you're missing one or more dependencies. Have you looked at the README and/or INSTALL files to see if any needed dependencies are listed?

---

### Post by Paqman on 2008-12-11
> **ubugross said:**
> Yi want to study source codes and is my interest to create the program from the source!

Ok, but there are some issues that come with compiling from source. Most importantly it breaks the dependency system of the package manager. This can lead to instability. If you want to compile from source a lot, you might want to do it in a sandboxed environment such as a virtual machine.

---

