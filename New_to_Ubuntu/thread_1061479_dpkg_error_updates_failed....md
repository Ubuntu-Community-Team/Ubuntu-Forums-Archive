---
title: "dpkg error updates failed..."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2009-02-05
this is what happens when i try to install updates through update manager...```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
```

ben@ben-desktop:~$ sudo dpkg --configure -a
[sudo] password for ben: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

What is happening here?? Is this happening to everyone or just me??

---

### Post by plucky on 2009-02-06
> What is happening here?? Is this happening to everyone or just me?? 


This [thread](http://ubuntuforums.org/showthread.php?p=6663769) might help or search the forums for  "dependtry"


Good Luck

---

### Post by clive littlewood on 2009-02-06
Hi

Just do what the error message tells you !!

Open a terminal and run "sudo dpkg --configure -a" without the qoutes.

And all will be fine             :D

Clive

---

### Post by az on 2009-02-06
Are you able to figure out which package is screwing things up?

Try 
sudo dpkg --clear-avail

then, 

sudo apt-get update

sudo apt-get -f install

---

