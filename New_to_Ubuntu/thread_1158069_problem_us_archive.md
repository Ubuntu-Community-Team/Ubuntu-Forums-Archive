---
title: "problem us archive"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-13
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by matey3 on 2009-05-13
which version?

---

### Post by shadowlands on 2009-05-13
I up graded from 8.04 LTS 	Hardy Heron 	to 8.10 	Intrepid Ibex 	2008-10-30.  I do not think it took, the upgrade because my screen after I log on is still a bird.

---

### Post by superprash2003 on 2009-05-13
what does , system->about ubuntu , say?

---

### Post by matey3 on 2009-05-13
Got to /etc/apt/ and rename your sources.list file
copy mine and name it sources.list
this one works;




#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by SunnyRabbiera on 2009-05-13
I would open up software sources (system > administration> software sources)
and change the settings on the ubuntu software tab.
Change the server in the "download from" pulldown menu to "main server"
works for me :D

---

### Post by shadowlands on 2009-05-13
That did not work.> **SunnyRabbiera said:**
> I would open up software sources (system > administration> software sources)
and change the settings on the ubuntu software tab.
Change the server in the "download from" pulldown menu to "main server"
works for me :D

---

### Post by shadowlands on 2009-05-13
Hardy Heron > **superprash2003 said:**
> what does , system->about ubuntu , say?

---

### Post by shadowlands on 2009-05-13
Thanks, but can you provide step by step directions on how to do this?  Thanks again.> **matey3 said:**
> Got to /etc/apt/ and rename your sources.list file
copy mine and name it sources.list
this one works;




#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by shadowlands on 2009-05-13
bump
> **shadowlands said:**
> Thanks, but can you provide step by step directions on how to do this?  Thanks again.

---

### Post by skymera on 2009-05-13
```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list 
```

paste and save.

```
 sudo apt-get update 
```

---

### Post by shadowlands on 2009-05-13
thanks
> **skymera said:**
> ```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list 
```

paste and save.

```
 sudo apt-get update 
```

---

### Post by shadowlands on 2009-05-13
I followed the up date directions on this page:[http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/).  Did I doa good thing or just cause my self more problems?

---

### Post by shadowlands on 2009-05-13
new problem: E: Type 'matey3' is not known on line 57 in source list /etc/apt/sources.list

---

### Post by shadowlands on 2009-05-13
> **shadowlands said:**
> new problem: E: Type 'matey3' is not known on line 57 in source list /etc/apt/sources.list
never mind

---

