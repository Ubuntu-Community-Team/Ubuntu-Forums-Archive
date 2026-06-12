---
title: "Update errors"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Falc7 on 2009-08-31
When i try and check for updates, i get these errors

Release.gpg  Could not resolve ‘packages.dfreer.org’

W: Failed to fetch [http://packages.dfreer.org/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://packages.dfreer.org/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘packages.dfreer.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by halitech on 2009-08-31
looks like packages.dfreer.org is down and trying to go to dfreer.org redirects to [http://cortana.dfreer.org:8080/](http://cortana.dfreer.org:8080/) which has a verizon logo and a log in screen on it

I would edit that source out for now and try to update

---

### Post by Falc7 on 2009-08-31
hhmm, i wonder what that dfreer thing is.
Now i get this message

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/jaunty/non-free/i18n/Translation-en_GB.bz2](http://download.virtualbox.org/virtualbox/debian/dists/jaunty/non-free/i18n/Translation-en_GB.bz2)  Could not resolve ‘download.virtualbox.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.


This was a new thing i found from here
[http://ubuntuforums.org/showpost.php?p=7614149&postcount=2](http://ubuntuforums.org/showpost.php?p=7614149&postcount=2)

---

### Post by wojox on 2009-08-31
You'll need to edit that one out as well. The link is dead.

---

### Post by halitech on 2009-08-31
can you post your sources.list file?
```
cat /etc/apt/sources.list
```

---

### Post by Falc7 on 2009-08-31
I edited virtual box out, and now i get this message upon reload:

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.


```
jamie@jamie-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# deb http://packages.dfreer.org jaunty main
# deb http://packages.dfreer.org jaunty main
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
jamie@jamie-laptop:~$ 

```

---

### Post by halitech on 2009-08-31
At this point I would suggest commenting out anything that does not have ubuntu or canonical and try updating again. The system is able to connect to the internet right?

---

### Post by Falc7 on 2009-08-31
yep, the machine i am getting these errors with is the same system i am writing to you now on. I'll try as you suggest

edit: yeah that worked, no error messages now, but i would like wine to keep itself updated, and be able to use 3rd party software sources in general

---

### Post by halitech on 2009-08-31
ok, if its working with the non ubuntu repos, the issues are with those repos. You can re-enable them but just be aware, if things go wrong, there is little anyone can do to figure them out short of commenting them out and see if things work again.

---

