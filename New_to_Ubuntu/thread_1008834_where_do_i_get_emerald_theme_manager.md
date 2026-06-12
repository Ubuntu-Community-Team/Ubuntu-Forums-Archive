---
title: "where do i get emerald theme manager?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-11
hey... im sure this is another total noob question but then again i am a total noob lol so.. where do i find the emerald theme manager? it is not in the repositories or under add/remove programs. where should i go for it? i googled it and nothing really came up for a download. 


thanks a bunch in advance guys!

---

### Post by adult swim on 2008-12-11
go to system>administration>software sources and make sure that the first four boxes are checked.  then go to a terminal, applications>accessories>terminal and then run ```
sudo apt-get update

sudo apt-get install emerald
```
once it installs it will be under system>preferences>emerald theme manager

---

### Post by 11010110 on 2008-12-12
also i installed it and got the theme i wanted ut it doesnt seem to be loading it onto my computer... any ideas?

---

### Post by EnGorDiaz on 2008-12-12
> **11010110 said:**
> also i installed it and got the theme i wanted ut it doesnt seem to be loading it onto my computer... any ideas?

alt f2

```
emerald --replace
```

---

### Post by 11010110 on 2008-12-12
thanks man worked like a charm!

---

### Post by icyest on 2008-12-28
This may be a newbish question, but how do you apply Emerald Theme Manager? Is this a theme creator? as in like a photoshop? or is it like compiz-fusion where it's just click and appear effects?

I've never used emerald before.


I just didn't want to start a new thread.


(also, since I used sudo apt-get install to forcefully get emerald, will it update by itself? or will i have to put in the repository address in sources.list?)

---

### Post by bwang on 2008-12-29
```

emerald --replace

```
to start emerald. Since you installed through apt-get, it will update itself.

---

