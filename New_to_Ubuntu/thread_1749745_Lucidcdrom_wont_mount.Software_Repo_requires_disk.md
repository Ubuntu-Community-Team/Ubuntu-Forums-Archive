---
title: "Lucid:cdrom wont mount.Software Repo requires disk"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by MisFitt on 2011-05-04
The dvd/cd rom otherwise works fine.This is the error I got after a lot of trouble after install and some updates:
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
This at top:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."
I had just wiped and re formatted after too many problems with Mint Isadora.I went back to having 10.04 rather than a Mint dual boot with Ubuntu 10.10.
If I can't fix this I'll have to wipe my disk and start again,again.I want stability in my OS no.1.
Thanks
Edit: I'm having difficulty finding terminal commands,which is what this is about I know.That's a priority in moving forward.

---

### Post by ivanovnegro on 2011-05-04
Ok, first of all, maybe you should uncheck the CD ROM from your repositories.
Go to Software Center-> Other software-> there should be your sources list where you can add new stuff, uncheck the first entry I think, CD ROM, you dont need this as a source. I hope that is your problem, normally its unchecked.
Then go to the entry where it says 404 error and remove it from there, this repo seems not to function anymore, its a Debian package.
Then try to update your system again.

---

### Post by MisFitt on 2011-05-04
Thanks,I've already done that-doesn't do anything.
It's a GPG Key error/issue.I can't install a lot of software because of this and it seems to have happenned to a few but I can't find any definative answers.
Thanks so much for your reply,appreciated

---

### Post by garvinrick4 on 2011-05-04
What does your sources.list look like:
```
gedit /etc/apt/sources.list
```

---

### Post by MisFitt on 2011-05-04
> **garvinrick4 said:**
> What does your sources.list look like:
```
gedit /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ftp.debian.org](http://ftp.debian.org) etch main
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) lucid main
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted

---

### Post by MisFitt on 2011-05-04
I don't know if this relevant but I enabled this medibuntu keyring at some stage:
[http://packages.medibuntu.org/lucid/medibuntu-keyring.html](http://packages.medibuntu.org/lucid/medibuntu-keyring.html)

---

### Post by garvinrick4 on 2011-05-04
If you are not using these put a # in front of them: sudo gedit /etc/apt/sources.list  (make changes and hit save)
If you are go to ppa's page at launchpad and get key to input.

deb [http://ftp.debian.org]("http://ftp.debian.org/") etch main
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) lucid main

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab")

---

