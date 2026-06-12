---
title: "CPP Sanity?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by The Flash on 2011-01-12
I wasn't sure if this is where it should go, as you can see, I'm still pretty new to the linux world.

I'm running 10.10 and whenever I attempt to 'make'  anything, I get the same error message:
```
/lib/cpp sanity check failed...
```Or something along those lines. My computer with ubuntu does not have an internet connection, otherwise I would check.

Sorry if this is the wrong area, it just seemed like a noob question!

---

### Post by JKyleOKC on 2011-01-12
You need to have the "build-essentials" package installed in order to compile things with makefiles, and getting it installed is likely to be difficult in the absence of an internet connection because this package is actually a link to a whole bunch of other packages that are necessary for compiling stuff.

Can you arrange an internet connection in order to install it? If you can, open Synaptic Package Manager, search for "build-essentials," select "mark for installation" and then click on "Apply" and follow the instructions that will appear. It will list a number of packages that will be downloaded, and once it completes the installation you should be able to make your programs.

However it's best, when possible, to use the pre-compiled packages from the repositories, rather than making from source. Doing so will get the packages documented in the "dpkg" database and make it much easier to keep them up to date, and to remove them when no longer desired...

---

### Post by The Flash on 2011-01-12
Thanks a bunch! I usually can but right now the snow outside is up to my knees!

I'll get on that as soon as I can.

Cheers!

---

### Post by Irihapeti on 2011-01-12
Unless things have changed recently, the "build-essentials" package is actually available from the live CD itself. In "software sources" in Synaptic Package Manager, there is an option to tick the CDROM as a source. If you do this and click on "reload", you should find that you can then select "build-essential" and it will load the packages from the CD.

I was on dialup for the first 18 months of my Ubuntu use, and this was extremely useful.

---

