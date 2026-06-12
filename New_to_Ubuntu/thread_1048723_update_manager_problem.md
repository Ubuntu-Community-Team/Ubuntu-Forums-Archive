---
title: "update manager problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by metici on 2009-01-23
Ok, hello. I have a problem, recently the update manager has not been working and neither has synaptic. When I try to open either of them, I get this message:



     Could not initialize the package information

     An unresolvable problem occurred while initializing the package information.

     Please report this bug against the 'update-manager' package and include the following error message:

     'E:Malformed line 51 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'



This just started recently, and I don't know why. Or how to fix it.

I'm running Ubuntu 8.10.

---

### Post by yeats on 2009-01-23
Fortunately, Linux error messages almost always contain a clue to the problem.  Can you open your /etc/apt/sources.list file and post the contents here?  You can type Alt-F2 and type 

```
sudo gedit /etc/apt/sources.list
```

Or you can open a terminal  and type the same command if that doesn't work.

---

### Post by metici on 2009-01-23
ok, I typed that into the terminal and this is everything that it brought up:


deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted multiverse universe #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) intrepid main
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) hardy main
deb [http://ubuntusoftware.info/intrepid](http://ubuntusoftware.info/intrepid) all
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe

---

### Post by yeats on 2009-01-23
Okay - you need to comment out (that is put a # in front of) or remove altogether, this line:

```
deb http://ubuntusoftware.info/intrepid all
```

That's not a valid repository that I know of - I wonder how it got in there?

make sure you save it, then try Synaptic again.

---

### Post by avtolle on 2009-01-23
While you are commenting that out, I suggest you comment out the ppa launchpad entries that refer to hardy as well. It is not a good thing to have sources for different releases in the /etc/apt/sources.list.

---

### Post by metici on 2009-01-23
wow, thanks I can access synaptic now. but when I go to update it gives me this error.


Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by avtolle on 2009-01-23
You need to comment out the first line which refers to the Hardy CD (sorry, I missed that the first time through).

---

### Post by metici on 2009-01-23
nevermind, I commented out all the hardy pp launches, and it fixed it. Thanks :D

---

