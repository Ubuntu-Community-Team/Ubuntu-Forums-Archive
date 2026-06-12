---
title: "Updating issue"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by lbarnes on 2009-01-16
Hey guys, i'm having an issue with a repository with my update manager
at the top it says the package information hasn't updated in 60+ days.
I get this error when i load the repositories:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release](http://archive.canonical.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

This looks like a pretty important repository lol
It does install other updates but apparently not the important system ones!

Thanks

---

### Post by adult swim on 2009-01-16
go to a terminal and enter in ```
cat /etc/apt/sources.list
``` and then paste that back here

---

### Post by lbarnes on 2009-01-16
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
lennon@lennon-desktop:~$

---

### Post by crjackson on 2009-01-16
disregard...

---

### Post by lbarnes on 2009-01-16
disregarded...

---

### Post by ibuclaw on 2009-01-16
> **lbarnes said:**
> 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free**

The item put in **BOLD** is all on one line ... split it down to fix that.
> 
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner**
**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse**
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted**
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

The ones in **BOLD** have already been mentioned once (this is at the bottom of the file), and I don't see the point of you keeping identical repositories from two different locations in your sources list. So you can delete those lines.

To edit it, type in:
```
sudo gedit /etc/apt/sources.list
```
Regards
Iain

---

### Post by lbarnes on 2009-01-16
sorry, i'm not sure what you mean by "split it down"

lol, i understand that now and it indeed fixed my problem - thanks

---

### Post by lbarnes on 2009-01-16
tried to give you thanks on the reply but it looks like it's gone now
been away awhile...

---

