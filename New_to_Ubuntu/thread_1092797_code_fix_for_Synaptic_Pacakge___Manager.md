---
title: "code fix for Synaptic Pacakge   Manager"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-03-10
How do I fix this:
 Type 'and' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
I guess I need to type something in the terminal, as that's how I messed it up I think, I hope there is some simple coding, had a rough day, not feeling so sharp right now :)  but I can't accomplish much without my Synaptic Package manager. thanks

---

### Post by yeats on 2009-03-10
Can you post the output of the terminal command:

```
cat /etc/apt/sources.list
```

?  That will reveal the problem :-)

---

### Post by yther on 2009-03-10
Did you run some "apt" command trying to add repositories to your sources?

Try opening /etc/apt/sources.list and look on line 48.  The answer will probably be obvious.  If it's not, get some sleep and look again tomorrow.  ;)

---

### Post by Lakeside5 on 2009-03-10
Yes Yther, I think I did lol
Here it is Chris, sorry it's so long!

~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical 

and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by yeats on 2009-03-10
```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical

and the respective vendors as a service to Ubuntu
```


You'll want to do

```
sudo gedit /etc/apt/sources.list
```

then put your cursor before the "and" you see here, and backspace until it's on the same line as "offered by Canonical."  Either that or remove the line altogether - it's not important to the file itself.

---

### Post by Lakeside5 on 2009-03-10
Ok, u can't see me but I'm doing my Happy Dance thanks to your help :) It was something  simple after all, like the space you said after AND (which the error message kept telling me, but I didn't understand lol). So I learned something too, this forum rocks, the manager is fixed  now thanks again!

---

### Post by yeats on 2009-03-11
> **Lakeside5 said:**
> Ok, u can't see me but I'm doing my Happy Dance thanks to your help :) It was something  simple after all, like the space you said after AND (which the error message kept telling me, but I didn't understand lol). So I learned something too, this forum rocks, the manager is fixed  now thanks again!

Happy to help - glad you're up and running again.

---

### Post by Lakeside5 on 2009-03-11
You're welcome guys :)

---

