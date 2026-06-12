---
title: "Consistent Update Error: Malformed Release file?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2011-01-04
I'm running into a consistent update error, which occurs no matter how I try and update (Terminal/Update Manager/Ubuntu Tweak).

Error is:

> W: Failed to fetch [http://deb.playonlinux.com/dists/jaunty/Release](http://deb.playonlinux.com/dists/jaunty/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

I have tried uninstalling and reinstalling PlayOnLinux but to no avail.  Think it may be time to consult you wise Linux Pros for some Terminal advice. ^^,

---

### Post by danielgrosvenor on 2011-01-17
I've found a few other instances of this problem online (such as here: [https://answers.launchpad.net/ubuntu/+source/apt/+question/44731](https://answers.launchpad.net/ubuntu/+source/apt/+question/44731) ) but I still don't know how to go about fixing this problem.

I'm happy to simply remove PlayOnLinux, which would presumably remove the problem.  But uninstalling it (via Ubuntu Software Centre) makes no difference; I still get this error message every time I try and update. :(

---

### Post by plucky on 2011-01-18
why are you using a Jaunty Repository when you are running Maverick.
Jaunty is no longer supported.

Please post output of ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

You should remove that source in **Software Sources** and then go [Here]( http://www.playonlinux.com/en/download.html) and use the correct command to install the correct repository for Maverick.

Good Luck

---

### Post by danielgrosvenor on 2011-01-18
> **plucky said:**
> why are you using a Jaunty Repository when you are running Maverick.
Jaunty is no longer supported.

Ah, well there is a very good reason for that: I am a total Linux n00b.

> **plucky said:**
> 
Please post output of ```
cat/etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```


```
dan@dans-dell:~$ cat/etc/apt/sources.list
bash: cat/etc/apt/sources.list: No such file or directory
dan@dans-dell:~$ ls -l /etc/apt/sources.list.d/
total 128
-rw-r--r-- 1 root root 138 2011-01-04 16:54 alecive-antigone-maverick.list
-rw-r--r-- 1 root root 138 2011-01-04 16:54 alecive-antigone-maverick.list.save
-rw-r--r-- 1 root root 174 2011-01-04 16:54 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root 174 2011-01-04 16:54 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root 154 2011-01-04 16:54 cybolic-vineyard-testing-maverick.list
-rw-r--r-- 1 root root 154 2011-01-04 16:54 cybolic-vineyard-testing-maverick.list.save
-rw-r--r-- 1 root root  71 2010-10-11 03:00 doctormo-barry-snapshot-lucid.list.distUpgrade
-rw-r--r-- 1 root root 110 2010-12-28 17:00 doctormo-barry-snapshot-lucid.list.save
-rw-r--r-- 1 root root 110 2011-01-04 16:54 doctormo-barry-snapshot-maverick.list
-rw-r--r-- 1 root root 110 2011-01-04 16:54 doctormo-barry-snapshot-maverick.list.save
-rw-r--r-- 1 root root  50 2011-01-04 16:54 dropbox.list
-rw-r--r-- 1 root root  50 2011-01-04 16:54 dropbox.list.save
-rw-r--r-- 1 root root  58 2011-01-04 16:54 getdeb.list
-rw-r--r-- 1 root root  58 2011-01-04 16:54 getdeb.list.save
-rw-r--r-- 1 root root 176 2011-01-04 16:54 google-chrome.list
-rw-r--r-- 1 root root 176 2010-10-11 03:00 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 2011-01-04 16:54 google-chrome.list.save
-rw-r--r-- 1 root root  83 2011-01-04 16:54 maverick-partner.list
-rw-r--r-- 1 root root  83 2011-01-04 16:54 maverick-partner.list.save
-rw-r--r-- 1 root root 306 2011-01-04 16:54 medibuntu.list
-rw-r--r-- 1 root root 269 2010-10-11 03:00 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 306 2011-01-04 16:54 medibuntu.list.save
-rw-r--r-- 1 root root 416 2011-01-04 16:54 opera.list
-rw-r--r-- 1 root root 416 2011-01-04 16:54 opera.list.save
-rw-r--r-- 1 root root 134 2011-01-04 16:54 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2011-01-04 16:54 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root 124 2011-01-04 16:54 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 124 2011-01-04 16:54 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root  89 2010-10-11 03:00 ubuntu-tweak-stable.list.distUpgrade
-rw-r--r-- 1 root root 124 2010-12-28 17:00 ubuntu-tweak-stable.list.save
-rw-r--r-- 1 root root 136 2011-01-04 16:54 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2011-01-04 16:54 ubuntu-wine-ppa-maverick.list.save

```

---

### Post by plucky on 2011-01-18
> Ah, well there is a very good reason for that: I am a total Linux n00b.


That is a lot of extra repositories for a noob.

The first command I gave was incorrect as it didn't have a space between cat and /etc.I have now corrected it.Please post the output from that command.

---

### Post by danielgrosvenor on 2011-01-18
Et voila:

```
dan@dans-dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb-src http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb-src http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports restricted main multiverse universe
deb http://deb.playonlinux.com/ jaunty main
deb-src http://deb.playonlinux.com/ jaunty main

```

---

### Post by plucky on 2011-01-18
> deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main
deb-src [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main

Try disabling those two lines.

To edit the file use ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of those two lines will disable those repositories.

Then run ```
sudo apt-get update
``` and see if you still get the warning message.

Good Luck

---

### Post by danielgrosvenor on 2011-01-18
VICTORY!!! :D

Thank you very much for your help, plucky!

---

