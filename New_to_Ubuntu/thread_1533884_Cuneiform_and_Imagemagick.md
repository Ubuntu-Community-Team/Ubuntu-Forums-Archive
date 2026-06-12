---
title: "Cuneiform and Imagemagick"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by jbr100uk on 2010-07-18
Hi everyone.  How do I get the Cuneiform OCR package to work with Imagemagick, so that it can convert a wide variety of images into text, rather than just BMP files?  Imagemagick was already installed on my system, so I installed Cuneiform 0.7 from the default Ubuntu 10.04 software repository.  Unfortunately, Cuneiform will only work with BMP files and not other image types, as I'd hoped. How do I get Cuneiform to recognize that I have Imagemagick installed?  Do I need to compile Cuneiform from source to do this?  If so, how should I go about doing this?

Many thanks for your help.

John

---

### Post by mbsullivan on 2010-07-19
Hi John,

Hmmm... My guess is that you DO have to recompile it to get it to work the way you're describing.

Trivially, you can convert almost any image format to a BMP yourself with Imagemagick:

```
convert [original file] [new file].bmp
```

Then proceed as normal with Cuneiform.

Mike

PS: Out of curiosity, I decided to give it a try on my machine with [this PDF]("http://www.eecs.berkeley.edu/Pubs/TechRpts/1983/CSD-83-121.pdf"). The results were not promising... it seg faults on many pages, and gives completely nonsensical results on those it doesn't crash on. Also, it has no manpage, a very poor interface, and seemingly no documentation to speak of. I hope you have better luck than me!

---

### Post by mbsullivan on 2010-07-19
Ok, so I looked into it some more, and if you actually want to use this program right now (which seems a bit questionable to me), you definitely want to use the bleeding edge version. This means compiling from source, so you might as well have support for all file formats.

The bleeding edge version is 1.0 (as opposed to 0.7.0). You can get it [here]("https://launchpad.net/cuneiform-linux"). Follow the following steps, more or less. I can fill in the gaps tomorrow if you want:

(1) Install libmagick++-dev:

```
sudo aptitude install libmagick++-dev
```

(2) Download the .tar.bz file to the right.

(3) Extract it

```
tar -xjf cuneiform-linux-1.0.0.tar.bz2
cd cuneiform-linux-1.0.0
```

(4) Read readme.txt, and follow the Unix installation directions. I had to delete the following check from CMakeList.txt to get it to stop complaining, but maybe that's just me:

```
if(PROJECT_BINARY_DIR STREQUAL PROJECT_SOURCE_DIR)
   message(FATAL_ERROR "In-tree build attempt detected, aborting. Set your build dir outside your source dir, delete CMakeCache.txt from source root and try again.")
endif()
```

So, the commands come down to something like the following, starting from cuneiform-linux-1.0.0/:

```
mkdir builddir
cd builddir
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=[wherever, or leave this part out] ../CMakeList.txt
cd ..
make
make install 
```

If you want to install it to /, do a "sudo make install" at the bottom. Also, you can speed up the make (which is quite slow) with "make -j N", where N is the number of processors you have in a multiprocessor system.

Mike

PS: I've still had no luck with it producing ANY meaningful results whatsoever, though it has stopped crashing now.

---

