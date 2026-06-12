---
title: "Repositories greyed out"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-21
I have this issue with 2 computers, one Win7/Ubuntu11.04 and the other Lubuntu.  After installing (or doing an upgrade/reinstall, I cannot access the repositories.  The access is unavailable in synaptic, software center, and via terminal.  

I seem to recall there was a post install command to transfer over to the software sources, but I cannot find it anywhere....

Can someone help me out?  Is that all I'm missing?

Thanks in advance!

---

### Post by _0R10N on 2011-06-21
Could you post your /etc/apt/sources.list file, please?

---

### Post by smcrossman on 2011-06-21
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ natty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ natty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb http://us.archive.ubuntu.com/ubuntu/ natty main universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main universe #Added by software-properties
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://download.virtualbox.org/virtualbox/debian natty contrib
deb-src http://download.virtualbox.org/virtualbox/debian natty contrib

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ natty-security restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-security restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
```

---

### Post by jerrrys on 2011-06-21
open a terminal and enter

sudo apt-get update

and see if it works now

---

### Post by dFlyer on 2011-06-21
After sudo apt-get update, you might want to uncomment out the following lines so you can get to natty partner like so.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

This can also be done through software center under preferences.

Just make sure to run sudo apt-get update again.

---

### Post by Rex Bouwense on 2011-06-21
I am not sure if you are aware of it but only one update method can be used at a time.  If you are using the Ubuntu Software Center, do not open the others.  Same with the other two.  If more than one is open then you will not be able to update.

---

### Post by smcrossman on 2011-06-21
Well, without doing anything other than running the diagnostic above....this one is fine now.  I will do the apt-get updates (I actually like installing that way but use the others to look for things to install). And I will do the recommended edit.  I haven't made it to the back to see what shape that one is in.  I will let you know when I know.

I keep forgeting that sometimes Ubuntu "adapts" to new apps or software more gradually rather than its not there and then it is.

---

### Post by smcrossman on 2011-06-21
Well, I have managed to update and install on both computers.  The one with Lubuntu....when you open Synaptic it opens as a non-root user and unless you go into it with root privileges it won't allow you to access the repositories or to apply any changes you've chosen.   Hmmm...new question! LOL  I'm brand new to Lubuntu so I have some researching and learning to do !

Oh and on the other it is quite possible I had multiple package installer apps open.  For some reason the darned thing will not run unity since the update (and the touchpad doesn't work either) so I'm a little lost figuring out what is open and isn't still open, and where it is.

---

