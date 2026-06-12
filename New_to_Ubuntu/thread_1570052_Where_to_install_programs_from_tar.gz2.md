---
title: "Where to install programs from tar.gz2?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Nostigex on 2010-09-07
So I've been looking through instructions on how to unpack and install programs from tar.gz, but none of them suggest *where*. If I simply followed the instructions, it seems to me like I would install the program in my downloads folder! (correct me if I'm wrong... perhaps the extracted tarball is comparable to a setup.exe from windows, which can be safely removed after installation?).

If installation is anything like windows, then the program keeps a collection of files in a designated folder, which in a windows setup.exe, would be chosen at some point during the installation process. Usually this is a subfolder within 'Program Files'. Is there an analogous folder in the Ubuntu file system? Or should I create a folder in my Home directory specifically for programs? Or have I got the whole idea mixed up?

---

### Post by davidmohammed on 2010-09-07
you usually "unzip" the file into a folder in your home folder.  You then untar the file.  Most of these kind of files have a "configure" and a "make" approach (you run these from a command line).  Finally you do a "sudo make install" - leave it to the defaults to install....


Most (but not all) of these kinds of files have been converted to "deb" files which you can install without compiling.  Most debs can be found by just looking in the software centre (or synaptic manager).  

What is it you are trying to compile?

---

### Post by Nostigex on 2010-09-07
There's nothing I need to install at the moment, though I've seen some programs from time to time that looked useful, that weren't in the repositories. So I thought I'd investigate...

---

### Post by Thelasko on 2010-09-07
It's been a while since I compiled software, but if I recall correctly, you can compile the software in any folder within your /home folder.  (untar the file into some folder, make, install, etc.)  When you are finished compiling, there should be a .deb file in that folder.  Then you install the .deb file as you would normally.

I've been lucky enough to find a [PPA]("https://help.launchpad.net/Packaging/PPA") for any hard to find software I've wanted to install in the past 2 years or so.

---

### Post by manny43 on 2010-09-07
Download file to Desktop

linuxbest.tar.bz2

open up terminal
type in cd Desktop
type in tar xjvf linuxbest.tar.bz2
it will create a new folder: linuxbest
type in cd linuxbest
type in ./configure
           make
           make install

---

