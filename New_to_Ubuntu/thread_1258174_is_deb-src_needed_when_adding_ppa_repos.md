---
title: "is deb-src needed when adding ppa repos"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by brookie on 2009-09-04
hello,
when adding repos from ppa like banshee; is the deb-src line also need to be added to the sources.list file necessary? 

for example:
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) intrepid main

or is the deb-src only for programers who want to and know how to modify source code?

---

### Post by bodhi.zazen on 2009-09-04
no

I do not use the deb-src (I always comment them out in all repos) unless I wish to compile from source.

99.99 % of the time when I compile for source I do not use the Ubuntu source code, I get the source code from the project home page (usually because I want a more up to date version then what is in the Ubuntu repositories).

---

### Post by brookie on 2009-09-04
thanks bodhi! you rock! 
have a great labor day weekend in montana!
:-)

---

