---
title: "error while updating by command line"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by aliov_85 on 2009-05-06
Hello,

When I execute > sudo apt-get update, I get the following:

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ir.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://ir.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ir.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://ir.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead. 

Thanks for any help

---

### Post by MontelEdwards on 2009-05-06
huh? those arnt even deb respos?
lol.


Well just edit your sources.list

um,
sudo gedit /etc/apt/sources.list
delete those lines
oh,
and an easier way would be just to go to application sources in gnome and do it. im too lazy to elaborate on that, but im sure you can figure it out.

---

### Post by collinp on 2009-05-06
They are the package lists to the Security repos. Not sure what/how this error would be generated, but my guess would be someone messed it up on the server side.

---

### Post by aliov_85 on 2009-05-06
Dear deonote,

Thanks for your reply, I couldn't figure out which lines I have to delete.

Here is the source list:

> 
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


Regards

---

### Post by Sealbhach on 2009-05-06
Your sources list looks OK to me. Looks like it's a server side error, I don't think you have to do anything but wait till it's fixed.


.

---

### Post by aliov_85 on 2009-05-06
Ok, I hope so

---

### Post by MontelEdwards on 2009-05-06
Ya, im sorry. I think that it may be sever error.
my bad ;)

---

