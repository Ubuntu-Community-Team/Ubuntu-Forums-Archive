---
title: "Problem with update manage"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-23
HI there i have a horrible problem,every time i try tp update ubuntu via the update manager,,,somewhere along the line it freezes my computer completely,,and ive tried much to fix it but have had no luck..please help

---

### Post by taurus on 2009-01-23
Which release are you using?  Is it x86 or x86_64 version?  What happens if you update it from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itsvan on 2009-01-23
im not sure,, i think im running the 64 bit version,, how can i check?

---

### Post by taurus on 2009-01-23
Applications -> Accessories -> Terminal
```
lsb_release -a
uname -a
```

---

### Post by Michael.Godawski on 2009-01-23
```
uname -a
lsb_release -a
```

it is not possible to beat taurus :)

---

### Post by itsvan on 2009-01-23
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
itsvan@HAL-3000:~$ uname -a
Linux HAL-3000 2.6.24-22-rt #1 SMP PREEMPT RT Mon Nov 24 21:01:16 UTC 2008 x86_64 GNU/Linux



When i tried using    sudo apt-get upgrade,,it was updating normally,,and again it froze my computer and i had to restart it,,it doesnt finish it all the way through..

---

### Post by taurus on 2009-01-23
> **Michael.Godawski said:**
> 
it is not possible to beat taurus :)

It is possible and doable.  Just bring it on...  ;)

---

### Post by taurus on 2009-01-23
Can you post the whole output of the **sudo apt-get upgrade** if you could?  Also, post your /etc/apt/sources.list too.

```
cat /etc/apt/sources.list
```

---

### Post by itsvan on 2009-01-23
#
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main





# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2009-01-23
> **itsvan said:**
> #
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main





# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

You are running hardy but then you have a few gutsy's repos in your /etc/apt/sources.list!  What's up with that?  And on top of that, you have automatix!!!  :shock:

If your machine has not trashed by now, it will soon.

---

### Post by Michael.Godawski on 2009-01-23
well I would comment out every entry with a gutsy in it with a # in front of it.

so open the sources.list with

```
gksudo gedit /etc/apt/sources.list
```

and add a # in front of every line with gutsy and leave only the hardy entries uncommented.

---

### Post by itsvan on 2009-01-23
WHAT DO I DOOOOOOOOOOOOOOOOOOOOOOOOOOOOooo??

---

### Post by Michael.Godawski on 2009-01-23
whaaa

remove the automatix entry completely.

then after cleaning up the file from all unnecessary stuff save the file and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itsvan on 2009-01-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


i get that when i want to upgrade,why?

---

### Post by taurus on 2009-01-23
Whatever program you ran to get that error message, close that first.  Then from a terminal, run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itsvan on 2009-01-23
Ya i tried it again,,but when it goes to the update it keeps on freezing after a while,i dont know what step of the download it is?

---

### Post by taurus on 2009-01-23
The cause could be because you have been using both gutsy and hardy repos on top of automatix.  It's like triple whammies there.  If I were you, I'd back up all my important files and do a clean install of hardy.

---

### Post by itsvan on 2009-01-23
#
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
#eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
#deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main







mayeb something there is still wrong??

---

### Post by Michael.Godawski on 2009-01-23
There are still gutsy entries in it.

Have a look a the source.list once more and be sure you comment out every gutsy entry with a #.

Then save and
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itsvan on 2009-01-23
do u think u can do that,and send it,,so i can paste it here.,,,,cus im pretty new at all this stuff

---

### Post by taurus on 2009-01-23
> **itsvan said:**
> #
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
#eb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb cdrom:[Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015)]/ gutsy main multiverse restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B][COLOR="Red"]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse[/COLOR][/B]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
#deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
#deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Wine
[B][COLOR="Red"]deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main[/COLOR][/B]


Put a # in front of those four entries.

---

### Post by itsvan on 2009-01-23
IT freezes every time it says updating password, or renewing password

---

### Post by taurus on 2009-01-23
Again, probably the best course of action for you is back up the important files and reinstall hardy from fresh since who knows how long you have mixed gutsy and hardy repos.

---

### Post by itsvan on 2009-01-23
ok thank you again..il prob need help doing that

---

