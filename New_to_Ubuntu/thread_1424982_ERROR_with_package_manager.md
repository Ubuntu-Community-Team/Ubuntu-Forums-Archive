---
title: "ERROR: with package manager"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by danielhughes77 on 2010-03-08
I have this error when trying to open package manager.

> E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by r-senior on 2010-03-08
Could you open up your /etc/apt/sources.list file with your text editor and paste the contents?

---

### Post by danielhughes77 on 2010-03-08
Forgive me if this is wrong I haven't had to put code on here yet
:DThanks

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main
deb http://ppa.launchpad.net/corenominal/ubuntu hardy main
deb http://download.skype.com/linux/repos/debian/stable non-free
```

---

### Post by agnes on 2010-03-08
Alter the last line to
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
You just missed a space between *.../debian/* and *stable*.

---

### Post by danielhughes77 on 2010-03-08
Sorry I don't understant.  You said I missed but I didn't do anything that I know of.  Could you give me the remedy.  Thanks alot:D

---

### Post by oldos2er on 2010-03-08
Run ```
gksu gedit /etc/apt/sources.list
``` in a terminal. Replace the last line with the line agnes gave you.

You've got a couple other problems you should change while you have that file open. Add a comment mark # in front of line 61, so that it looks like "# deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) hardy main" (without the quote marks). Mixing different versions' repositories is not a good idea; it usually confuses the hell out of the package manager.

Replace the "YOUR_UBUNTU_VERSION_HERE" in lines 54 and 55 with "karmic"

Save and exit the file, then run ```
sudo apt-get update
```

---

### Post by danielhughes77 on 2010-03-09
First off that was fun :) I love command line and linux.
Second off it worked and I didn't even know what I did.

When you say I should never mix versions how did I even do that?

Having issues with top menu
[B]EDIT: I have the app, places menu but it is in the middle with firefox to the left and I would like the places to the left and then firefox to the right of that menu.
[/B] 
Though my error is gone :D

---

### Post by oldos2er on 2010-03-09
> **danielhughes77 said:**
>  I have the app, places menu but it is in the middle with firefox to the left and I would like the places to the left and then firefox to the right of that menu.


 Right-click on the panel where you want a particular launcher or icon, add it with 'Add to Panel....' Once you've done that you can delete the old entries you no longer want.

It's probably best to start a new thread when you have a question on a different subject.

---

### Post by MichealH on 2010-03-09
> **danielhughes77 said:**
> First off that was fun :) I love command line and linux.
Second off it worked and I didn't even know what I did.

When you say I should never mix versions how did I even do that?

Having issues with top menu
[B]EDIT: I have the app, places menu but it is in the middle with firefox to the left and I would like the places to the left and then firefox to the right of that menu.
[/B] 
Though my error is gone :D

You dunno what you did let me tell you:

If you get the PPA wrong It cannot get anything for that software and could break apt-package managers until that is fixed and It was sort of severe that so It broke your package manager i guess.

---

### Post by danielhughes77 on 2010-03-16
> Right-click on the panel where you want a particular launcher or icon, add it with 'Add to Panel....' Once you've done that you can delete the old entries you no longer want.

When I right click and add panel to add firefox it is not listed in the list.

---

