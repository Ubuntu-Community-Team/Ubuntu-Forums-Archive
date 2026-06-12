---
title: "amazon.con downloader"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by protpisys on 2010-08-27
Hey...I was trying to get an mp3 album downloaded from Amazon but couldn't get the downloader installed. I kept getting the error message:

Error: Dependency is not satisfiable: libboost-filesystem1.34.1

is there a workaround for this or am I doing something wrong...again. I noticed the software is for Ububtu 9.04 and I'm using 10.04 but I'm guessing that isn't it. Thanks.

---

### Post by iMisspell on 2010-08-27
You can try and open up a terminal window and key in the following to do a search.
```
aptitude search libboost-filesystem
```

With Lucid (10.04), i get:
> p   libboost-filesystem-dev                                       - filesystem operations in C++ (default version)                          
p   libboost-filesystem1.40-dev                                   - filesystem operations (portable paths, iteration over directories, etc) 
p   libboost-filesystem1.40.0                                     - filesystem operations (portable paths, iteration over directories, etc) 


_

---

### Post by Zzl1xndd on 2010-08-27
This worked for me

[http://ubuntuforums.org/showthread.php?t=1478214](http://ubuntuforums.org/showthread.php?t=1478214)

---

### Post by oldos2er on 2010-08-28
Try [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

