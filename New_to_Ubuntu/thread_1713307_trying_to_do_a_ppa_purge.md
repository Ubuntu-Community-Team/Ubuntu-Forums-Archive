---
title: "trying to do a ppa purge?"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by adduds on 2011-03-23
Got this on a sudo apt-get update
```

W: Failed to fetch http://ppa.launchpad.net/pms-client-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/pms-client-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

so i installed ppa-purge.deb

Then ran 


```
ad@desktop:~$ sudo ppa-purge ppa:pms-client-team/ppa
PPA to be removed: pms-client-team ppa
Warning:  Could not find package list for PPA: pms-client-team ppa
```


am i doing something wrong or wtf?

---

### Post by beew on 2011-03-23
Since you haven't installed anything there is nothing to purge. If you don't want the ppa any more you can just remove it from your sources list.

ppa purge is for safely downgrading packages that you have installed from the ppa(and then remove the ppa)

---

### Post by adduds on 2011-03-24
i don't see it anywhere.....

do you?

```
# 
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse


```

---

### Post by beew on 2011-03-24
Check the directory /etc/apt/sources.list.d  There should be a file for the ppa. Just delete it.

---

### Post by adduds on 2011-03-24
ah thanks very much a nice clean apt-get update :P

whats the difference between the two?

---

