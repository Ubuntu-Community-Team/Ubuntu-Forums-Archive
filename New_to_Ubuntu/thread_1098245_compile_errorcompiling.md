---
title: "compile error/compiling"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by nargilamonster on 2009-03-16
Hi All,
Total n00b here. I'd like to know in general, what the compiling process is like and how one can do it easily since many apps that I see online are (only) available as source code. In particular, when I tried to compile a file I got this error messsage:

```

[$] ./configure
checking build system type... powerpc-unknown-linux-gnu
checking host system type... powerpc-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I tried 'sudo ./configure' but that didn't work any differently.

thanks!

---

### Post by taurus on 2009-03-16
Have you installed the build-essential package?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by nargilamonster on 2009-03-16
sweet! that worked really well! I'm only missing a few packages, can I also usse apt-get to acquire these too?

```

checking pkg-config is at least version 0.9.0... yes
checking for pkghildon... no
checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

```

---

### Post by taurus on 2009-03-16
Yes.  Looks like you need ncurses.  Do a Search in synaptic if you are not sure about the names.

---

### Post by nargilamonster on 2009-03-16
this is what happens when i try to get ncurse:

```

$ sudo apt-get ncurses
E: Invalid operation ncurses

```

---

### Post by kk0sse54 on 2009-03-16
> **nargilamonster said:**
> this is what happens when i try to get ncurse:

```

$ sudo apt-get ncurses
E: Invalid operation ncurses

```

You're running apt-get without any commands such as for example "install", what the previous poster suggested was opening up Synaptic and searching for all ncurses related packages that you might need.

---

### Post by binbash on 2009-03-17
sudo apt-get install libncurses5-dev

---

### Post by MindController on 2009-07-27
I still have one problem guys. When i did what C!oud told, it's ok but i typed the make command it appered 
```
make: *** No targets specified and no makefile found.  Stop.
```
Where can i find that file or what should i do? Please
sorry for my bad english, BTW

---

