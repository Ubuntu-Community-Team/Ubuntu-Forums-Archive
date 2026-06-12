---
title: "Package dependency: Can't read error message (trying to install SDL_Image)"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Vyse86 on 2010-03-03
Hi,


I get the following error when trying to install libtiff4-dev:

> libtiff4-dev:
  Depends: libtiff4 (=3.8.2-11) but 3.8.2-11ubuntu0.9.04.3 is to be installedI have libtiff4 3.8.2-11 installed on my system. And generally absolutely no idea what this message means. 

EDIT: The full version number is actually "3.8.2-11ubuntu0.9.04.3" - so maybe it looks for 3.8.2-11 but only finds 3.8.2-11ubuntu0.9.04.3, getting confused by the suffix that should not be there?

Is there an alternate way to install SDL_Image? I'm currently trying to install it with "sudo apt-get install libsdl-image1.2-dev" because there is no manual on how to compile it from source. Well, there is, but it just says "unpack and build" i.e. it's not very helpful to somebody who relied on Synaptic so far :???:

Even if I knew, I'd probably have to set a flag to leave out IMG_tif.c or else it will just crash at some point later on.

---

### Post by diesch on 2010-03-03
> **Vyse86 said:**
> 
I get the following error when trying to install libtiff4-dev:

I have libtiff4 3.8.2-11 installed on my system. And generally absolutely no idea what this message means. 

EDIT: The full version number is actually "3.8.2-11ubuntu0.9.04.3" - so maybe it looks for 3.8.2-11 but only finds 3.8.2-11ubuntu0.9.04.3, getting confused by the suffix that should not be there?

This suffix is part of the version number so "3.8.2-11ubuntu0.9.04.3" is not the needed version "3.8.2-11".

What does
```
  apt-cache policy libtiff4 libtiff4-dev 
```
print?

> **Vyse86 said:**
> 
Is there an alternate way to install SDL_Image? I'm currently trying to install it with "sudo apt-get install libsdl-image1.2-dev" because there is no manual on how to compile it from source. Well, there is, but it just says "unpack and build" i.e. it's not very helpful to somebody who relied on Synaptic so far :???:


The package *libsdl-image1.2* contains the files you need to *run* a program that needs libsdl-image1.2 and the package* libsdl-image1.2-dev* the files you need to *compile* a programm that needs libsdl-image1.2. You don't need it to compile from source.

---

### Post by Vyse86 on 2010-03-03
> 
libtiff4:
  Installed: 3.8.2-11ubuntu0.9.04.3
  Candidate: 3.8.2-11ubuntu0.9.04.3
  Version table:
 *** 3.8.2-11ubuntu0.9.04.3 0
        100 /var/lib/dpkg/status
     3.8.2-11 0
        500 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) jaunty/main Packages
libtiff4-dev:
  Installed: (none)
  Candidate: 3.8.2-11
  Version table:
     3.8.2-11 0
        500 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) jaunty/main Packages
With compiling from source, I mean the archive you can get here: [http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)

---

### Post by mc4man on 2010-03-03
You should ck. System -> Software sources -> Updates and make sure the first 2 listed are enabled (security and updates

If both aren't enabled then do so, click close and reload, then try again

If both were then  just try
```
sudo apt-get update && sudo apt-get install libtiff4-dev
```

---

### Post by Vyse86 on 2010-03-03
#-o

sudo apt-get update. Of course. Even I as a noob should have known that ;)

Thanks.

---

