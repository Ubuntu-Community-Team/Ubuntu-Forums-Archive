---
title: "graphics-magick install problem"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Pertinax on 2010-08-14
I'm trying to use phoronix test suite, but I run into a problem trying to install the cpu suite. It can't download the graphics-magick from any of the mirrors. For each mirror, this message appears:

Attempting to re-download from another mirror.
            Downloading: GraphicsMagick-1.3.7.tar.bz2         [6.27MB]
PHP Warning:  fopen([http://internap.dl.sourceforge.net/sourceforge/graphicsmagick/GraphicsMagick-1.3.7.tar.bz2):]("http://internap.dl.sourceforge.net/sourceforge/graphicsmagick/GraphicsMagick-1.3.7.tar.bz2%29:") failed to open stream: HTTP request failed!  in /usr/share/phoronix-test-suite/pts-core/library/pts-functions_net.php on line 83

The MD5 check-sum of the downloaded file is incorrect.
Failed URL: [http://internap.dl.sourceforge.net/sourceforge/graphicsmagick/GraphicsMagick-1.3.7.tar.bz2](http://internap.dl.sourceforge.net/sourceforge/graphicsmagick/GraphicsMagick-1.3.7.tar.bz2)


I went and downloaded graphics-magick 1.3.7 and executed the configure, make, make install process. However, I still can't run the cpu suite. any suggestions?

---

### Post by Paul820 on 2010-08-14
Did you install the test suite through synaptic package manager? There is also graphicsmagic in synaptic.

---

### Post by Pertinax on 2010-08-14
I already have synaptic package manager, but I did not get phoronix through it.

---

### Post by Paul820 on 2010-08-14
If you install phoronix and graphicsmagick through the package manager instead of downloading and building them off the internet, anything they need (dependencies) will be automatically installed for you.

---

### Post by Pertinax on 2010-08-14
I've gone through and completely removed phoronix through synaptic, then re-installed it. Then, I installed graphics magick through synaptic also. However, I am still running into the same problem. Thanks for all of your help so far!

I am running phoronix through terminal, so when I want to try to run the cpu test I enter

cicero@cicero-laptop:~$ phoronix-test-suite run cpu
PHP Notice:  Use of undefined constant IS_NVIDIA_LINUX - assumed 'IS_NVIDIA_LINUX' in /usr/share/phoronix-test-suite/pts-core/objects/phodevi/components/phodevi_system.php on line 1052

============================================================
graphics-magick is not installed.
To install, run: phoronix-test-suite install graphics-magick
============================================================

Would you like to install these tests now (Y/n)? 

Which then brings me to the downloading/mirror problem. This still happens after I have downloaded graphicsmagick through synaptic.

---

### Post by Paul820 on 2010-08-14
Apparently downloading your own software through synaptic doesn't work anyway.
> The Phoronix Test Suite will automatically download all needed test files. In addition, on supported platforms it will also use the distribution's package management system for installing the needed test dependencies. However, for the software being tested that may be installed already on the system by the user, the Phoronix Test Suite will ignore those installations. The Phoronix Test Suite installs all tests within its configured environment to improve the reliability of the testing process. This ensures all tests being used are at the same version, being run or built from the same source packages, and minimizes outside changes such as patches or build-time optimizations that may be specific to a single distribution or environment. This does, however, result in additional download time and extra disk space needed. If installing a large test suite, it may consume several gigabytes of disk space.
I got to the downloading part but it wanted to download 2Gb of data off the net so i stopped it. :confused:

All i can suggest is to check out their forums: [http://www.phoronix.com/forums/forumdisplay.php?f=49]("http://www.phoronix.com/forums/forumdisplay.php?f=49")

---

### Post by Pertinax on 2010-08-14
Will do. Thanks again.

---

