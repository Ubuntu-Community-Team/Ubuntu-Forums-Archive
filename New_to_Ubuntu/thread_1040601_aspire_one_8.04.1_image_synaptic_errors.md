---
title: "aspire one 8.04.1 image synaptic errors"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by TonyBenson on 2009-01-15
hi

i am having problems with my aspire one running 8.04.1.

whenever i run sudo aptitude update, or sudo apt-get update, or using the synaptic package manager i recieve multiple 404 errors.

i have searched for this over the forum, and i have found no solution, i have recreated my sources.list, ensure i am putting at a uk mirror.

any help would be most welcome as I dont want to completely reinstall.  this problem is stopping me installing new programs.

cat out put is 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

sources.list as below

# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-security multiverse

results of sudo aptitude update using above sources.list

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
  404 Not Found
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/main Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/restricted Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/universe Packages
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-security/multiverse Packages
  404 Not Found


any help gratefully accepted.
Tony

---

### Post by TonyBenson on 2009-01-16
bumping because i really need assistance on this.

---

### Post by pmthien on 2009-01-16
Hi guy,
Should you try sudo apt-cdrom after insert you CD 8.04 LTS in your cdrom

I faced with this issue before.

Good luck
Thien

---

### Post by TonyBenson on 2009-01-16
I dont have a cd rom drive.  This is an acer aspire one netbook.  I installed via an image written to usb from another ubuntu laptop which has since died as it got covered in water so I cannot recreate the usb stick from there

---

