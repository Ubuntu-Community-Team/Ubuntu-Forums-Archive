---
title: "Repository Issue"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by gwilkins82 on 2010-04-30
Been having this problem for a long time, but now it is stopping me from upgrading to 10.04, so I'd like to fix it.  When I check for upgrades, I get two errors about sources:

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.45 80]

(in case these links get shorted, they are /dists/karmic/main/binary-1386/Packages.gz and another with /universe instead on /main

What is my issue?  I don't see these sources in my source list:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) karmic main
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) karmic main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic main universe
deb-src [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main

Anybody know how to resolve this?  Thanks!

---

### Post by DougieFresh4U on 2010-04-30
Why don't you try making a new [sources list]("http://repogen.simplylinux.ch/")

---

### Post by gwilkins82 on 2010-04-30
> **DougieFresh4U said:**
> Why don't you try making a new [sources list]("http://repogen.simplylinux.ch/")

That looks like a great option...stupid noob question though.  How do I save my new source list - I can't simply copy and paste because that isn't done w/ the sudo command therefore I don't have permission.

---

### Post by P4man on 2010-04-30
faulty one in red. Add /ubuntu to it:

> **gwilkins82 said:**
> 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted universe main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) karmic main
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) karmic main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main
[COLOR="Red"]deb [http://archive.ubuntu.com**/ubuntu**](http://archive.ubuntu.com**/ubuntu**) karmic main universe[/COLOR]
deb-src [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main


edit: how do I make the forum NOT parse URLs ?

---

### Post by philinux on 2010-04-30
+1 p4man for good eyesight

---

### Post by gwilkins82 on 2010-04-30
> **P4man said:**
> faulty one in red. Add /ubuntu to it:



edit: how do I make the forum NOT parse URLs ?

Ok, this looks like the issue but again, stupid noob question - how do I make this change to the list?  I cannot just open it up in gedit and save it because I don't have permission.  Thanks!!

---

### Post by P4man on 2010-04-30
open a terminal (or press alt f2) and type

```
gksudo gedit /etc/apt/sources.list
```

gksudo launches the editor (called gedit) with root privileges.

If you want to this easier/often, you may want to install this little plugin:

```
sudo apt-get install nautilus-gksu
```

That will let you right click files or folders in the file manager and open them as administrator (root). Need to log out before it works.

---

### Post by gwilkins82 on 2010-04-30
Awesome.  Thanks for the info.  I'll post an update once I try all this stuff.

---

### Post by gwilkins82 on 2010-04-30
Sweet.  Worked like a charm.  Working on getting better at using the terminal.  Thanks again!

---

