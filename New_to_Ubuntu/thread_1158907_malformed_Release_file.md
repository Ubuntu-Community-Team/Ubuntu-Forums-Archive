---
title: "malformed Release file?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by BUKRITYA on 2009-05-14
Hy all. I am hoping to help out here one day too. Now, however I still feel like a newb although this is my third release...

trying to upgrade to Jaunty I first get a message saying third party sourced disabled, which I assume is ok. I then receive the message: W:Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://il.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb/source/Sources in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

and then it fails to proceed. 

```
/$ cat etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://il.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://il.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://il.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://il.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://il.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://il.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://il.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates


deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

```
I have also tried to change the server for a close by server for no avail. I think I might have a network problem.
Thank you Ubuntu Gurus. I don know how you do it.

---

### Post by Didius Falco on 2009-05-14
Hi,

I think I might have spotted the problem.

What you posted contains the following line:[FONT=monospace]
[/FONT]```
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates

```Notice how it's all in one string? Try editing your sources file and make it look like this:
```
deb-src http://il.archive.ubuntu.com/ubuntu/ intrepid
deb http://za.archive.ubuntu.com/ubuntu/ intrepid-updates
```Then run this in a Terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

I hope it helps....

Regards,

Didius

---

### Post by BUKRITYA on 2009-05-17
Hey Didius Falco,
Thank you for your reply. it now says ```
 sudo apt-get update && sudo apt-get upgrade
E: Malformed line 55 in source list /etc/apt/sources.list (dist parse)

```

which is this line: deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) intrepid 

it seems that the other lines have more details after "intrepid".

Would love some help....

---

### Post by Miljet on 2009-05-17
That seems to be the offending line (if I counted right). I would try just commenting out that line and see what happens. Just place a hash (#) at the beginning of the line. If it doesn't work, it is easy enough to change back.

---

### Post by waspbr on 2009-05-17
I think there is something missing from that line, maybe when you edited it before, you pasted the line over the word that used to be there...


I have been looking at my sources list but I can't  seem to figure out what to put there... perhaps try to comment it out (add a # at the beginning of line 55 [or even line 56 too])?

---

### Post by BUKRITYA on 2009-05-18
It is now working fine! thank you everyone for your help.
It was waspbr's advice that finally worked, and you are probably right about me messing with these lines... I just don seem to recall me editing these lines, and don't know exactly how it got this way...
however, I am wondering whether these now commented lines were of some importance to any other updates and sources.
What do you guys think?

---

### Post by waspbr on 2009-05-19
I don't think so, all the important lines seem to be ok, so I think you are safe.

Anyway glad everything is working now, enjoy the ride

---

