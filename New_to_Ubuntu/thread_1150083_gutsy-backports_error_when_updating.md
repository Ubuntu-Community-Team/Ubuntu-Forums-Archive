---
title: "gutsy-backports error when updating"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by tuskpc on 2009-05-05
I update my system last week, via the internet, and an error keeps occurring:

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

I checked the source.list and have this:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://astromirror.uchicago.edu/ubuntu/ jaunty main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-updates main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://astromirror.uchicago.edu/ubuntu/ jaunty universe
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://astromirror.uchicago.edu/ubuntu/ jaunty multiverse
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://astromirror.uchicago.edu/ubuntu/ jaunty-security main restricted
deb-src http://astromirror.uchicago.edu/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-security universe
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://astromirror.uchicago.edu/ubuntu/ jaunty-proposed restricted main multiverse universe #Added by software-properties
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-backports restricted main multiverse universe
deb-src http://astromirror.uchicago.edu/ubuntu/ jaunty-backports restricted main multiverse universe #Added by software-properties
deb http://astromirror.uchicago.edu/ubuntu/ jaunty-security multiverse

```

What can I safely delete, or modify, in this or some other part of the system?

---

### Post by mprince on 2009-05-05
I don't think Gutsy is supported anymore.

---

### Post by zvacet on 2009-05-05
If you want to have backports repos then replace gutsy in that line with Jaunty like this

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

Save and close file.

```
sudo apt-get update
```

Second option is not to use backports and in that case let that lines look

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

Save and close.

```
sudo apt-get update
```

---

### Post by tuskpc on 2009-05-06
Appreciate the help, it works now.

---

