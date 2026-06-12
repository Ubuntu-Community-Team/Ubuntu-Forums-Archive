---
title: "Failed to fetch repositories"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by NoonienSoong97 on 2010-01-16
I have looked around the site for information on this subject before posting. I found out that my sources.list is empty. Not sure how that happened. So I take it this is the problem to why I can't fetch from the repositories? I remember awhile back having to alter the sources.list file so I could do a test using the i386 binaries making sure my nvidia driver would stay connected after an update. I have had few updates ever since, and this was before karma came out, and the system I am using had a major update. The inability to update started about 20 days ago.

---

### Post by drs305 on 2010-01-16
If you are sure your sources.list is empty, you can use this site to generate a new one. It is safe to use.

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

If you want to confirm your sources.list is in fact empty, you can type this in a terminal window to check:
```
cat /etc/apt/sources.list
```

---

### Post by kenuf on 2010-01-16
Go to System> Administration> Software Sources
and make sure that everything that should be checked is checked.

For me it was the first 4 under Ubuntu Software, the one for the CDRom
And the canonical partner ones under the Other Software tab.

---

### Post by NoonienSoong97 on 2010-01-17
ok the cat function did show a list of repositories in the file. I am using Ubuntu 8.04. I know that version shouldn't be out of date yet. Last I check it was sometime in 2011 when it will be out of date.

Yea I made sure that the appropriate repository links were clicked in the Software sources window.

---

### Post by NoonienSoong97 on 2010-01-17
Here is what the cat showed:

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy main restricted
deb-src [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy universe
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy multiverse
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-security universe
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-backports restricted main multiverse universe
deb-src [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-backports restricted main multiverse universe
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-security multiverse

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
nooniensoong97@nooniensoong97-desktop:~$

---

### Post by drs305 on 2010-01-17
What happens when you run this in terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by NoonienSoong97 on 2010-01-18
As for using the update, and upgrade at the same time. All the other links either had ing, or hit. here are the links that failed.

Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/main Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/restricted Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/restricted Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/main Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/multiverse Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/universe Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/universe Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy/multiverse Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/main Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/restricted Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/restricted Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/main Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/multiverse Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/universe Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/universe Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-updates/multiverse Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/main Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/restricted Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/restricted Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/main Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/multiverse Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/universe Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/universe Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-security/multiverse Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/restricted Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/main Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/multiverse Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/universe Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/restricted Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/main Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/multiverse Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-proposed/universe Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/restricted Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/main Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/universe Packages
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/restricted Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/main Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/multiverse Sources
  404 Not Found
Err [http://ubuntu-mirror.cs.colorado.edu](http://ubuntu-mirror.cs.colorado.edu) hardy-backports/universe Sources
  404 Not Found
W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/main/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/restricted/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/main/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/multiverse/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/universe/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-proposed/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by drs305 on 2010-01-18
At the moment that server only seems to have hardy multiverse and restricted, which is why your system is producing all the "not found" errors.

Try changing servers in Synaptic or Software Sources. Settings, Repositories; Ubuntu Software. Then select a new server from the "Download From" window. Refresh the repository list by pressing the "Reload" button on Synaptic's main menu.

---

### Post by NoonienSoong97 on 2010-01-19
Yea that worked I used the main server to get my computer updated. However doesn't each server have a different format for Ubuntu?

---

