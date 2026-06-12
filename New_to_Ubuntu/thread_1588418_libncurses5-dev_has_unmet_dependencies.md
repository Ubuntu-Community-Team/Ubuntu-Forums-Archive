---
title: "libncurses5-dev has unmet dependencies"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by noncentz303 on 2010-10-04
Hello Everyone,

I am trying to install libncurses5-dev because I would like to utilize my tv tuner card. I was retrieving my drivers and I got this error for 1 of the packages.

The following packages have unmet dependencies:
  libncurses5-dev: Depends: libncurses5 (= 5.7+20090207-1ubuntu1) but 5.7+20090803-2ubuntu2 is to be installed
E: Broken packages

I have checked my /etc/apt/sources.list and everything seems ok but I did use a script to automate a bunch of different applications I use.

Any thoughts as to what this error might be?

Thanks for the help,

Noncentz

---

### Post by noncentz303 on 2010-10-04
Nevermind.... my sources.list was not in good shape thanks to medibuntu. I overwrote my sources.list with the default for Karmic and that did the trick.

---

