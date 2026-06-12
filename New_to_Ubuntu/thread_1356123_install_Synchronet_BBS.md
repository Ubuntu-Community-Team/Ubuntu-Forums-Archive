---
title: "install Synchronet BBS"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by ibjoe on 2009-12-15
I have been playing with Ubuntu and I need a little help.

I work long hours and cannot seem to find the time to fully explore ubuntu... ergo I want to install some software that I currently understand and I'll work outward from there.

Having said this I would like to install Synchronet BBS on my ubuntu machine.  There are some instruction and I cannot seem to make it work.

[http://www.synchro.net/docs/sbbsunix.txt](http://www.synchro.net/docs/sbbsunix.txt)

it seems to fail with the gmake command to build the program...

ideas!!!

---

### Post by lisati on 2009-12-15
Do you have "build-essential" installed? You might want to try: ```
sudo apt-get install build-essential
```

---

### Post by ArigornStrider on 2011-02-01
I'm guessing you have figured this out at some point in the last year, but this can be fixed in 10.04 and 10.10 by replacing the "gmake" with "make" in the instructions provided on that site.

lisati is correct that you need to have the build-essential packages to install this.

---

### Post by heron7 on 2011-02-01
Is that a virtual desktop with cloud storage , like Ubuntu one ?... 
[http://synchronet.com/virtualization_solutions/](http://synchronet.com/virtualization_solutions/) 
 
and Glide os ?.. but unix like Jolicloud :KS?....

---

