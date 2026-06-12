---
title: "Trying to install printer"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Sphynx718 on 2009-08-04
I finally found a manufacturer made linux driver for my canon mp630 in a .deb package no less only to realise that they (like so many others) have only catered for 32bit users (i386). However I did notice a source file in the downloads section and was thus wondering if it is possible for me to compile the source myself for my 64bit version of ubuntu. And if so, what programs and what commands will I need?

Link to driver downloads: [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP630%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP630%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

NB: my previous thread on this failed due to issues with ubuntu's securtiy protection preventing me from manually copying files.

EDIT: Also, perhaps there is a way to force install the 32bit drivers on a 64bit system?

---

### Post by Sef on 2009-08-04
Yes, check out this [thread]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by Sphynx718 on 2009-08-09
Well I couldn't get ubuntu to accept non-x64 packages no matter what I did so i gave up and downgraded to x86. So while the packages will at least try to install, i've hit another problem.

The package "IJ Printer Driver Ver. 3.00 for Linux (debian Package for MP630series)" won't install without " IJ Printer Driver Ver. 3.00 for Linux (debian Common package)". So i go to install that, only to find that it needs something called "libsys2". Which upon searching via the package manager I find that its already installed... (I did notice that libcupsys2 wasn't install prior to ubuntu updating itslf from a clean install.)

However, in a strange twist, I happened to try and install the common driver again later, only for the package manager to report that it was already installed...:shock: I then proceeded to install the mp630 specific driver without issue and I now have a working printer!

At last, goodbye windows...ahahahahaha. 

You have no idea how long i've wanted to say that.

---

