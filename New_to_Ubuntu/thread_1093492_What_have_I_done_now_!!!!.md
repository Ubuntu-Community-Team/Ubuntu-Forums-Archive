---
title: "What have I done now !!!!"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by jamesburns on 2009-03-11
I was only trying to learn, honest.

jim@jim-desktop:~$ sudo apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
jim@jim-desktop:~$ sudo apt-get install
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
jim@jim-desktop:~$ 


This is my source list. Many thanks for any help

jim@jim-desktop:~$ cp /etc/apt/sources.list ~/Desktop/sources.lis
jim@jim-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates restricted main main'
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main restricted
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb [http://archive.ubuntu/hardy](http://archive.ubuntu/hardy) main
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main'
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main' main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
jim@jim-desktop:~$

---

### Post by taurus on 2009-03-11
> **jamesburns said:**
> I was only trying to learn, honest.

jim@jim-desktop:~$ sudo apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
jim@jim-desktop:~$ sudo apt-get install
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
jim@jim-desktop:~$ 


This is my source list. Many thanks for any help

jim@jim-desktop:~$ cp /etc/apt/sources.list ~/Desktop/sources.lis
jim@jim-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates restricted main main'
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy multiverse
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security main restricted
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy-security multiverse
deb [http://archive.ubuntu/hardy](http://archive.ubuntu/hardy) main
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) hardy main**[COLOR="Red"]'[/COLOR]**
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted **[COLOR="Red"]main'[/COLOR]** main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
jim@jim-desktop:~$

You need to edit /etc/apt/sources.list and try to remove the ones in red.

---

### Post by LowSky on 2009-03-11
and please use ```
 tags when giving information from a terminal or list... thank you, It just makes reading them much easier

it will look like this when posted

[code] sudo apt-get update && sudo apt-get upgrade
```
its the button that looks the this **#**

---

### Post by kanikilu on 2009-03-11
<Mythbusters' Adam Savage voice>Well there's yer problem:
> deb [http://archive.ubuntu/hardy](http://archive.ubuntu/hardy) main

Change that to > deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main

---

### Post by jjacobs2 on 2009-03-11
It would probably work if you just remove the apostrophe from that line.

---

### Post by chriskin on 2009-03-11
> **jamesburns said:**
> 
deb [http://archive.ubuntu/hardy](http://archive.ubuntu/hardy) main

i think that this is the malformed line it talks about

hardy shouldn't have been in the blue line, there should be a space before it.


also, what are you trying to do with the sudo apt-get install command?
you need to specify an application
like sudo apt-get install {this app}


EDIT :  wow, it only took me two minutes to write it and so many have already answered 

kanikilu has a more complete approach than me either way :P

---

### Post by KIAaze on 2009-03-11
```
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
```
The error message says line 56 which is:
```
deb http://archive.ubuntu/hardy main
```

If you compare it to the other lines, you'll notice that a space is missing.
It should be:
```
deb http://archive.ubuntu/ hardy main
```

However, this won't probably be work either since [http://archive.ubuntu/](http://archive.ubuntu/) is not a valid URL.

It should be:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main
```
which you already have at line 59. So you can just delete line 56. :)

---

### Post by chriskin on 2009-03-11
> **taurus said:**
> You need to edit /etc/apt/sources.list and try to remove the ones in red.

just line 56 has a problem , or are we (me and those who said the same with me) wrong? there is not mentioned that those have a problem , do they?

---

### Post by kanikilu on 2009-03-11
> **chriskin said:**
> just line 56 has a problem , or are we (me and those who said the same with me) wrong? there is not mentioned that those have a problem , do they? No I think you guys are right about the apostrophe's as well, it just hasn't spit out an error for those yet because it encountered the bad URL on 56 first. I think...

---

### Post by chriskin on 2009-03-11
> **kanikilu said:**
> No I think you guys are right about the apostrophe's as well, it just hasn't spit out an error for those yet because it encountered the bad URL on 56 first. I think...
(i wrote about only 56, but i understand what you mean in defense of the other idea, thanks )

---

### Post by jamesburns on 2009-03-11
::popcorn:All sorted thanks to you all

---

