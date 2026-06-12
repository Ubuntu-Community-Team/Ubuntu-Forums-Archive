---
title: "Trying to learn"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by BruceAlmighty71982 on 2009-12-18
Trying to learn how to write my own source list

---

### Post by switch10 on 2009-12-18
Welcome to the forums!!

This is an awesome way to start making a customized sources.list [http://a2b-net.com/tips/sourceslistgenerator](http://a2b-net.com/tips/sourceslistgenerator)

---

### Post by switch10 on 2009-12-18
sorry here is the proper link.. 

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by xifer on 2009-12-18
That's a handy link above.  But in case you find something odd you want to add or tweak
the file is in /etc/apt/sources.list and you can use your favourite editor.

My file is pretty standard since I upgraded to 9.10 and is full of comments and stuff but typical lines look like this


```


deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe

deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
##deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
##deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports restricted main multiverse universe
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/loell/ppa/ubuntu karmic main

```

so you can see each line prefixed by # is not actually a command but a comment
you can edit out the # to cause the  line to be read by the interpreter
each line is just a type then a location then the name(s) of the releases.

---

