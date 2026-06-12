---
title: "missing software"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by mamamac on 2009-05-29
hey gang,
i tried to download and install wine, but it failed. i got an error message, then when i followed the instructions, i got this

deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb [http://wine,budgetdedicated.com/apt](http://wine,budgetdedicated.com/apt) hardy

what does it mean and how do i fix it? 

                    thanks

---

### Post by Didius Falco on 2009-05-29
Hi,

That error means the CD is listed as a software source, but it isn't in the CDRom.

Go to **Systems/Administration/Software Sources**, go to the **Third Party Sources** tab and uncheck the box nest to the listing for the CD.

When you close it, it well tell you it needs to reload the software sources - let it.

Then you can install Wine.

Regards,

Didius

---

### Post by x33a on 2009-05-29
do as didius said. 

or

just put a # in front of this line in the sources file.
> deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted

and also,

the last deb line has an illegal url, and it is duplicate of the one 2 lines before it. put a # in front of it too, and reload the sources.

to edit the sources file
```
gksudo gedit /etc/apt/sources.list
```
to reload the sources
```
sudo aptitude update
```

---

### Post by Didius Falco on 2009-05-29
> **x33a said:**
> do as didius said. 

or

just put a # in front of this line in the sources file.


and also,

the last deb line has an illegal url, and it is duplicate of the one 2 lines before it. put a # in front of it too, and reload the sources.

to edit the sources file
```
gksudo gedit /etc/apt/sources.list
```to reload the sources
```
sudo aptitude update
```

+1 Nice catch!! I missed that "," in the last line. Too focused on the CD thing...

Regards,

Didius

---

### Post by mamamac on 2009-05-29
thanks for responding. i must be a "DO IT WRONG" bean cause i'm unable to put an # in the software sources. the "ADD" button failes to light up. however i unchecked the cdrom, and got more error messages. i then removed the 2 wine lines, ran the codes above, and its working again, but i still dont have wine. what am i missing, not doing, and not getting?

                                   thanks

---

### Post by nandemonai on 2009-05-29
```
sudo apt-get install wine
``` ? ;)

---

### Post by mamamac on 2009-05-29
nandemonai cudos to you. simply devine.  many thanks to all for your help.  we be gettin now!

---

