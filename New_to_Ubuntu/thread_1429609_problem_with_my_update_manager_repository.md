---
title: "problem with my update manager repository"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by tversteeg on 2010-03-14
So whenever I try to update my comp I keep getting this error message Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
I'm a complete noob so please try to dumb it down for me thanks?

---

### Post by Elfy on 2010-03-14
You have an edgy repo in there for some reason. 

You'll need to remove that and try again.

Edit - if you have no idea what I mean please post your sources list here for someone to look at

Run this from a terminal (Apps > Accessories)

```
cat /etc/apt/sources.list
```

---

### Post by zeroseven0183 on 2010-03-14
I believe you're still using the old Ubuntu 6.10 Edgy Eft based on the link you posted?

---

### Post by zeroseven0183 on 2010-03-14
To remove that, open a Terminal and type
```
gksu gedit /etc/apt/sources.list
```then enter your password as required.

Look for the line in that file that says
```
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz
```and delete it. Save the file and exit.

Then type ```
sudo apt-get update
``` to update/refresh the list.

---

### Post by tversteeg on 2010-03-14
# deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
thanks for the help

---

### Post by zeroseven0183 on 2010-03-14
> **tversteeg said:**
> # deb cdrom:[Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
[SIZE=2][COLOR=Red]**deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe**[/COLOR][/SIZE]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
thanks for the help

That needs to go: [SIZE=2][COLOR=Red]**deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)  edgy universe**[/COLOR][/SIZE]

---

### Post by tversteeg on 2010-03-14
worked like a charm thanks

---

### Post by zeroseven0183 on 2010-03-14
That's good to know! Can you please mark this thread as SOLVED?
It's my pleasure helping you... :-)

---

### Post by mgco on 2010-03-15
Failed :(

---

### Post by halitech on 2010-03-15
> **mgco said:**
> Failed :(

what failed?

---

### Post by mgco on 2010-03-15
@[halitech]("http://ubuntuforums.org/member.php?u=69393") i'm having the same roadblock except that when i checked via terminal {cat /etc/apt/sources.list} it apparently shows that my updates are getting from Karmic sources. I tried running {sudo apt-get update}, but it still failed (just like in the GUI). what am i doing wrong?

Btw, I'm using Eee 900 (4GB + 16GB SSD), I just installed Karmic tonight replacing Jaunty. Got excited I finally got bluetooth running (in reference to the original bundled xandrOS distro which I had outgrown already)


Sharing:

[COLOR="DeepSkyBlue"]deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse[/COLOR]

---

### Post by slakkie on 2010-03-15
Would be handy if you told us what failed. We cannot look on your screen.

Anyways, a complete list of karmic sources:

```

### Karmic 9.10
# Required
#deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
# Recommended
#deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
# Optional
#deb http://packages.medibuntu.org/ karmic free non-free
#deb-src http://packages.medibuntu.org/ karmic free non-free
#deb http://archive.canonical.com/ubuntu/ karmic partner
#deb-src http://archive.canonical.com/ubuntu/ karmic partner
#deb http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Taskwarrior
# http://taskwarrior.org/projects/show/taskwarrior/
#deb http://ppa.launchpad.net/ultrafredde/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ultrafredde/ppa/ubuntu karmic main

## Virtual box
#deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```

And try to run apt-get update again.

---

### Post by halitech on 2010-03-15
when you run sudo apt-get update, what is the error you are getting? please post the entire output

---

### Post by mgco on 2010-03-18
@[slakkie]("http://ubuntuforums.org/member.php?u=116199") @[halitech]("http://ubuntuforums.org/member.php?u=69393")

The error that came up during reload was a dialog box stating "Error getting... (lists the files etc)"

Anyways, I replaced 9.04 with 9.10 Desktop Ed. & I think I may have found a possible reason for these errors: that I'm behind a proxy server - maybe that's why I was experiencing this roadblock.

---

