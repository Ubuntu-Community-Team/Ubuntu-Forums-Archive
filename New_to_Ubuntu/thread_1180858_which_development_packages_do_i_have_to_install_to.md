---
title: "which development packages do i have to install to install xautoclick?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by khfrekek on 2009-06-07
okay i am trying to install a program i found, xautcoclick, and in the install file, it says: "Be sure you have the proper development packages for your distribution
installed (i.e. something like xserver-xorg-dev, gtk2-dev, et cetera)." and then when i run ./configure, the build doesnt work.

does anyone know which dev packages i need to install to make this work?
thanks!

Oh and when i run ./configure, terminal says this:


Checking for c compiler ... gcc
Checking for c++ compiler ... can't find g++
Checking for gcc as c++ compiler ... no, disabling compilation of all c++ code
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... not found (check if the dev(el) packages are installed
Checking for X11 ... no
Checking for XTest extension ... no
No X11 found. Not building anything that depends on it

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick : no
cAutoClick : no
gAutoClick : no
gAutoClick2 : no
qtAutoClick : no

Installation to /usr/local

test: 785: ==: unexpected operator
Now type 'make' to build.



then when i run make, it says this:


make: Nothing to be done for `all'.

any help would be AWESOME!
Thanks :D

---

### Post by keplerspeed on 2009-06-07
The development packages allw you to 'compile' or 'build' the software. These need to be installed first. So go to synaptic, or open a terminal, and ensure all the packages that are required, and mentioned in the install file, are installed on your machine.

If you need a hand, just paste the relevant section of the install file here.

---

### Post by khfrekek on 2009-06-07
Hm well this is all the install file says:

$Id: INSTALL 62 2008-10-17 11:34:25Z ivovp $

Be sure you have the proper development packages for your distribution
installed (i.e. something like xserver-xorg-dev, gtk2-dev, et cetera).

After that, run:

./configure
make
sudo make install

So im not sure exactly which ones it wants me to install

---

### Post by keplerspeed on 2009-06-07
Ah.. you have been trying to install this for a while. khfrekek, you have started a new thread the same as yesterdays [http://ubuntuforums.org/showthread.php?t=1179327](http://ubuntuforums.org/showthread.php?t=1179327)

Just bumping your old thread would suffice. but not too often though! Your problem is not obscure, you patience will make it easier to find help.

---

### Post by keplerspeed on 2009-06-07
Ok from the ./configure output, you will need g++, xserver-xorg-dev and gtk2-dev.

To install these input this code to the terminal:

```

sudo aptitude install g++ xserver-xorg-dev python-gtk2-dev

```

Then run ./configure again.

---

### Post by khfrekek on 2009-06-07
oh ya i did, haha sorry, im just used to other forums who don't allow bumping, so i just made a new thread, ill just bump next time though, thanks :) okay so i went and installed those, and its almost working! heres what it said:

zack@Olympus:~/Firefox Downloads/xautoclick-0.20-src$ ./configure
Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... yes (using /usr/include)
Checking for X11 ... yes (using -L/usr/lib -lX11 -lXext)
Checking for XTest extension ... no
X11 found, but it does not seem to have the XTest extension
No X11 dependant applications will be build

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : no
cAutoClick    : no
gAutoClick    : no
gAutoClick2   : no
qtAutoClick   : no

Installation to /usr/local

test: 785: ==: unexpected operator
Now type 'make' to build.


oh and by the way, thanks so much for the help :D

---

### Post by keplerspeed on 2009-06-07
The output shows:

Checking for extra headers ... no
Checking for extra libraries ... no

and:

Checking for XTest extension ... no
X11 found, but it does not seem to have the XTest extension
No X11 dependant applications will be build

This means we need a few more packages. However, im not sure atm what they might be, ill see if I can find out. Anyone else know what we need?

---

### Post by keplerspeed on 2009-06-07
Ok try this:

```

sudo aptitude install libxcb-xtest0 libxcb-xtest0-dbg libxcb-xtest0-dev

```

And then ./configure

---

### Post by khfrekek on 2009-06-07
hmmm okay, well i searched for X11 in synaptic, and it found alot of results, maybe i need to install one of those?

---

### Post by keplerspeed on 2009-06-07
Try my above packages.

---

### Post by khfrekek on 2009-06-07
Okay i tried them and it said the same thing :( sorry

---

### Post by khfrekek on 2009-06-07
okay i think i figured it out!!! i found another guy who had the same exact problem as mine, and he fixed it, so i installed the packages he installed, and the make, and sudo make install commands actually worked this time, and there was no errors! do you know how i actually run the program now though? :o

---

### Post by khfrekek on 2009-06-07
nevermind, i found it! yay!!! it works!! :D thanks so much for all your help!! :)

---

### Post by Darhuuk on 2009-06-07
Could you please elaborate on which packages you had to install? I can't seem to find any info on Google and I'm having no luck so far with compiling xAutoclick.

---

### Post by kikeonline on 2009-10-08
Solution:

```
sudo apt-get install xorg-dev
```

```
make clean
./configure
sudo make install
```

Goes with some little errors but it install.

godd luck.

---

### Post by mic1099 on 2010-08-20
> **keplerspeed said:**
> Ok try this:

```

sudo aptitude install libxcb-xtest0 libxcb-xtest0-dbg libxcb-xtest0-dev

```And then ./configure

Hi I have same problem but when I try to install these packages install process want to remove 13 packages and there are some I really don't want to remove

---

### Post by oldos2er on 2010-08-20
It would be best for you to start a new thread, and post the complete terminal output you need help with.

---

