---
title: "Could not download all repository indexes!"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by graemebothwell on 2009-11-25
Hi Forum, 

I'm having problems with my updates, after installing the brilliant dropbox. I also tried to install chromium, after dropbox, but it didn't install. Dropbox is working fine, but can't update, annoying. I've more than likely screwed up my sources list, (see below, and under that text, is the error for downloading the repositories. I'd appreciate your help, and some advice on changing the sources list in the future please. :)

deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic main
deb-src [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic maindeb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main






The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by pi.boy.travis on 2009-11-25
> **graemebothwell said:**
> Hi Forum, 

I'm having problems with my updates, after installing the brilliant dropbox. I also tried to install chromium, after dropbox, but it didn't install. Dropbox is working fine, but can't update, annoying. I've more than likely screwed up my sources list, (see below, and under that text, is the error for downloading the repositories. I'd appreciate your help, and some advice on changing the sources list in the future please. :)

deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic main
deb-src [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) karmic maindeb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main






The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Hmm. . . There seems to be a problem with the dropbox links.  See if you can't update after commenting out those lines, with the # symbol.  If that works, double check the validity of the links.

Hope this helps. . .

---

### Post by MelDJ on 2009-11-25
> **graemebothwell said:**
> 
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/maindeb/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/source/Sources.gz)  404  Not Found
Failed to fetch [http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz](http://linux.getdropbox.com/ubuntu/dists/karmic/karmic/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

probably their server is down

---

### Post by HeadHunter00 on 2009-11-25
It doesn't look like a proper repository to me. Aren't ubuntu repositories supposed to have deb or deb-src before their name?

---

### Post by graemebothwell on 2009-12-14
> **pi.boy.travis said:**
> Hmm. . . There seems to be a problem with the dropbox links.  See if you can't update after commenting out those lines, with the # symbol.  If that works, double check the validity of the links.

Hope this helps. . .

pi.boy.travis, 
Finally able to sort out the problem due to changing internet provider, and what you suggested worked a treat, many, many thanks.

Cheers

---

