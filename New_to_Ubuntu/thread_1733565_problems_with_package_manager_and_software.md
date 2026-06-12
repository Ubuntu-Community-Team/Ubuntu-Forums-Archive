---
title: "problems with package manager and software"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by foolsgold7 on 2011-04-19
hi
cant get programs from package manager or software centre, i get the following error

SystemError: E:Type ‘eb’ is not known on line 21 in source list /etc/apt/sources.list, E:The list of sources could not be read.

any help would be much appreciated

---

### Post by ~Plue on 2011-04-19
could you post the output of *cat /etc/apt/sources.list* from a terminal

---

### Post by foolsgold7 on 2011-04-19
Hi Cheers for the prompt reply, as requested:

dave@dave-laptop:~$ cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
eb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) Lucid Lynx main
deb-src [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) Lucid Lynx main

---

### Post by arochester on 2011-04-19
Missing d in second last line. It should read deb.

---

### Post by ~Plue on 2011-04-19
run the following*; ```
gksu gedit /etc/apt/sources.list
```  *and comment out the last two lines (put a # infront of each). its not generally a good idea to use ppa's intended for other releases than the one you currently have. if you're sure it wouldn't cause any trouble, instead, put a d in front of line 21 as arochester noted

then run *sudo apt-get update* to refresh the software index

on a side note, the drapper desktop version reached end of life in 2009, so it might be better to back up and re install  a newer supported release

---

### Post by foolsgold7 on 2011-04-19
hi
thanks for all your help!!!

working now

---

