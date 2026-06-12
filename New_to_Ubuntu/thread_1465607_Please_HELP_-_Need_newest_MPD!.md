---
title: "Please HELP - Need newest MPD!"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by arrrghhh on 2010-04-29
So the version from the repo's is evidently borked, and I need to upgrade to at least v0.15.6.  The repo version is .4, and the current stable build is .9.

So I'm trying to add a repo, and I think my sources.list is hosed now because whenever I try to do an apt-get update, it fails... even when I comment out the repo's I added, it still fails!

So here's my sources.list:
```
# 
# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04 _Lucid Lynx_ - Beta i386 (20100406.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

#PS3 Media Server Repo
#deb http://deb.paissad.net/ unstable main contrib non-free
#deb-src http://deb.paissad.net/ unstable main contrib non-free
#deb http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main
#deb-src http://ppa.launchpad.net/paissad/pms-linux/ubuntu lucid main

#libzen0 libmediainfo0 for above
# deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#MPD bleeding edge
# deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu lucid main

#More MPD Stuff
#deb http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
#deb-src http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu lucid main
```

Note I commented out the ppa's for MPD... however... When I apt-get update -
```
sudo apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/gmpc-trunk/mpd-trunk/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://archive.canonical.com lucid/partner Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/mpd-trunk/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

So even with those repo's commented out, apt-get update is still failing seemingly on those repo's... What can I do?  How can I get the latest MPD without compiling - I don't want to have to recompile every time there's an update!!  Thanks!

---

### Post by arrrghhh on 2010-04-29
Solved.  Reference [this](http://ubuntuforums.org/showthread.php?t=1460338) thread if you want an explanation or a monaural conversation.

---

