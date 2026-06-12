---
title: "Installing Packages"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by mikeody on 2011-01-01
Am a bit confused.
I successfully unpacked a .gz tarball with tar xvzf - a package name folder was created  in the same directory.
I understood the next stage in installation is to cd to the package name folder and then ./configure.
The cd works OK but when I ./configure I get "no such file or directory".
Why is that ?
Thanks.

---

### Post by TeoBigusGeekus on 2011-01-01
Perhaps the package doesn't have a configure script.
Does it mention so in the installation instructions?
If so, re-download the package.

---

### Post by QLee on 2011-01-01
> **mikeody said:**
> Am a bit confused.
I successfully unpacked a .gz tarball with tar xvzf - a package name folder was created  in the same directory.
I understood the next stage in installation is to cd to the package name folder and then ./configure.
The cd works OK but when I ./configure I get "no such file or directory".
Why is that ?
Thanks.

Quite often a tarball like that which is intended for installing software will have a readme file included. Since you have cd'd to the folder of the unpacked tarball try a ls to see what files are there.

If one wants more specific help it can be useful to mention the name of the software that one is trying to install, sometimes there are specific things that need to be done and sometimes there are other solutions.

---

### Post by mikeody on 2011-01-02
Thanks guys,
Guess I was being a bit too 'simplistic'.
There was a file called 'build.txt' which then referred to another file called 'INSTALL' that had the installation instructions.
It was quite complex [for me at least !] but all worked out OK.
Lesson learned ! Thanks again.

---

