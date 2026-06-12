---
title: "Ubuntu 10.10"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by velzevool on 2010-10-20
How do i upgrade?Do i have to download ubuntu again or is there an other way?Also should i format?I don't wanna lose any data :)

---

### Post by SpinningAround on 2010-10-20
> **velzevool said:**
> How do i upgrade?Do i have to download ubuntu again or is there an other way?Also should i format?I don't wanna lose any data :)

```
sudo apt-get dist-upgrade 
```
would work I guess, depending on from what version you are upgrading from.
I never personally upgrade.

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by velzevool on 2010-10-20
Well actually i don't have a reason to upgrade,i'm just having an issue (well kinda) when the amount of free ram drops and doesn't come back to normal no matter if i close all the things i'm running.But anyway.Is there an app that will help me do it or should i upgrade hoping that i won't have this prob?

---

### Post by SpinningAround on 2010-10-20
> **velzevool said:**
> Well actually i don't have a reason to upgrade,i'm just having an issue (well kinda) when the amount of free ram drops and doesn't come back to normal no matter if i close all the things i'm running.But anyway.Is there an app that will help me do it or should i upgrade hoping that i won't have this prob?

Unsure about the RAM issue, maybe it's caused by a memory leak. 10.04 will receive updates to April 2012 since it's a LTS version.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

EDIT: Do you know what program that are causing the memory problem?
10.04 might be supported longer then April 2012, LTS give 3 so maybe it should be April 2013.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by philinux on 2010-10-20
> **velzevool said:**
> Well actually i don't have a reason to upgrade,i'm just having an issue (well kinda) when the amount of free ram drops and doesn't come back to normal no matter if i close all the things i'm running.But anyway.Is there an app that will help me do it or should i upgrade hoping that i won't have this prob?

What does the command
free -m
show?

---

### Post by QIII on 2010-10-20
> **SpinningAround said:**
> EDIT: Do you know what program that are causing the memory problem?

It may not be a memory problem at all.  It may be a well-understood, intended and desirable feature of Unix-like systems.  "Memory leak" has a very specific meaning in Computer Science.

Hence, philinux' question.

---

### Post by velzevool on 2010-10-20
total       used       free     shared    buffers     cached
Mem:          4024       1465       2559          0         46        377
-/+ buffers/cache:       1041       2983
Swap:         6234          0       6234

Actually this [img]http://img409.imageshack.us/img409/4485/screenshot3g.png[/img]

---

