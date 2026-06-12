---
title: "Problem with Ubuntu 7.1"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by aharp52 on 2009-06-02
I need to make larger some of the folders created when I installed u7.10 from cd.  Friom what I can see, that means repartitioning in linux speak.  However, when I try to install Gpartition (don't remember the exact name) as well as a lot of other programs listed as being available, I get the message that the program doesn't support a 386 computer.  Since I have an AMD 2600 CPU, I don't understand why I get that message or what I can do about it.  Evidently, the partition manager is what I need to fixd the microscopicly small folder created upon installation?

---

### Post by halitech on 2009-06-02
Did you install the AMD64 version or the x86 version? You can't mix and match versions as they are developed for the machine type and won't run on the other.

Also, you can't resize a partition thats mounted so I would suggest getting the gparted live cd and using that to resize your partitions instead.

---

### Post by LowSky on 2009-06-02
the partition editor is on the livecd, no need to install it to make your partitons bigger.

63bit version wouldn't be able to start up on a 32bit processor, so I cant see why you have this error.

Also 7.10 is not supported anymore, please use a newer version, like 8.04 or 9.04

---

### Post by bodhi.zazen on 2009-06-02
The partition editor is called gparted.

here is a guide on how to use it :

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Partitions should be managed from a live CD.

and last, ubuntu 7.10 is no longer supported (FYI) so you may wish to back up your data and install 8.04 (LTS) or 9.04 (most recent).

---

