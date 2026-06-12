---
title: "Malformed line 68"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-25
E:Malformed line 68 in source list /etc/apt/sources.list (dist parse)

I have looked every where for help with this so now I am posting on the board.  Can some one help me with this or give me a link or search terms to find solution? 

Thanks

---

### Post by Gazneth on 2009-05-25
It looks like line 68 has a error like spelling or a missing space maybe. To look at it open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```
Count down to line 68, it should be formed in a similar manner as your other sources. Here is a copy of my sources list if that will help you compare.

> 

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by shadowlands on 2009-05-25
bump

---

### Post by shadowlands on 2009-05-25
I tip my hat to you and say thank you ever so much for your help.> **Gazneth said:**
> It looks like line 68 has a error like spelling or a missing space maybe. To look at it open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```
Count down to line 68, it should be formed in a similar manner as your other sources. Here is a copy of my sources list if that will help you compare.

---

### Post by Gazneth on 2009-05-25
Just happy to help. Cheers!

---

### Post by Drate on 2009-05-27
Perhaps mark as solved?

---

### Post by philinux on 2009-05-27
> **Drate said:**
> Perhaps mark as solved?

That feature is now not available. Been like that for months. Same with thanks, that went to.

---

### Post by NHArticleTen on 2009-05-27
> **Drate said:**
> Perhaps mark as solved?

not only that...but...

post the problem and the solution that worked...

after all, it's all part and parcel of the "pay it forward" way...

---

### Post by Didius Falco on 2009-05-27
Here is a little tip to help you with the tedious "count the lines" part of dealing with this, if you use gedit:

Go to **Edit/Preferences** and the **View** tab and tick the box next to **Display Line Numbers**.

Much easier than the finger on the screen, scroll down..."Crap!! Lost count, start over!!" method.

Regards,

Didius

---

### Post by Celauran on 2009-05-27
You can do the same in vim with :set number

---

### Post by oldos2er on 2009-05-27
Or use Search, Go to line....

---

### Post by Cheesemill on 2009-05-27
Or
```
:68
```
:)

---

### Post by shadowlands on 2009-05-28
What is a vin number set.And the tab to mark solved is missing.> **Celauran said:**
> You can do the same in vim with :set number

---

