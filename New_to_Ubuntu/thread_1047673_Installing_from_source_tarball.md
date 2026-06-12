---
title: "Installing from source tarball"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by MadsRH on 2009-01-22
I really didn't know where to post this question (feel free to move it if it's out of context).

I'm trying to install [Rakarrack]("http://rakarrack.sourceforge.net/dl.html") on Ubuntu 8.10, but there seems to be a lot of dependencies and I can find them i Synaptic :(
[Here's the tarball...]("http://sourceforge.net/project/showfiles.php?group_id=215888")
This is where the ./configure currently stops:

```
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
configure: error: Alsa is required

```

Would it make a difference if I installed this on Ubuntu Studio? or should I try to find a similar application that is more user-friendly?

I found a [forum thread with an old PPA]("http://sourceforge.net/forum/forum.php?thread_id=2665443&forum_id=778862") (version 2 and the current is ver 3), but cannot run. It get: **Cannot make JACK client, is JACKD running?**

Thanks

---

### Post by vhegos on 2009-01-22
From the look of the error message you do not have alsa installed.  Install alsa ([www.alsa-project.org/main/index.php/Main_Page](www.alsa-project.org/main/index.php/Main_Page)) and then run the config script again.

---

### Post by notquitemichael on 2009-01-22
actually what you probably don't have is the development librarys of alsa.

i'd reccomend you look in synaptic of alsa-dev or libalsa.

this is because you ofton compile programs in ubuntu from synaptic without taking their libraries. then if you need to compile something from source that uses another library (in this case alsa's sound,) then you need to install the libraries or development files. normally you'll find these as [program]-dev, or lib[program]

-tom.

---

### Post by zvacet on 2009-01-22
@ **MadsRH**

From terminal go to the directory where you downloaded source and run

```
sudo apt-get build-dep package_name
```

That should give you all dependencies you will need to compile.

---

### Post by MadsRH on 2009-01-22
Thanks for all the reply'. I got ALSA working by installing *libasound2-dev*, but X11 is still not working.
[U]
zvacet[/U] -> What package name should I write? **sudo apt-get build-dep package_name**


Here's the latest output from ./configure:
```
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating data/Makefile
config.status: creating icons/Makefile
config.status: creating doc/Makefile
config.status: creating doc/help/Makefile
config.status: creating doc/help/imagenes/Makefile
config.status: creating doc/help/css/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands

```

---

### Post by joseangelini on 2009-01-22
perhaps you should install libxpm-dev package
sudo apt-get install libxpm-dev 

Good luck

---

### Post by snova on 2009-01-22
Additionally install **libjack-dev**.

---

### Post by MadsRH on 2009-01-23
Thanks, I think that will solve it :-)


I'll just test...

---

### Post by zvacet on 2009-01-23
> What package name should I write? sudo apt-get build-dep package_name

The one you are trying to compile.In your case it is rakarrack.

---

### Post by joseangelini on 2009-01-23
When you download the sources files belongs to a package, for example mozilla-firefox,  with
 
apt-get source mozilla-firefox

this command: apt-get build-dep mozilla-firefox
 

will check with the source file and download/install the dependencies needed to compile it

---

