---
title: "Update not working--don't know which software source to disable"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by fordguydude on 2010-06-01
I've been having the same trouble as many people on here, with updates not working correctly. It looks like the fix is disabling a software source. The error message I get is this--

```
Failed to fetch http://ppa.launchpad.net/zach/ppa-zach/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead. 
```

These are my software sources "other updates" tab. 

[img]http://img189.imageshack.us/img189/6231/screenshotsoftwaresourch.png[/img]

I don't know which one to disable that I haven't already disabled.

---

### Post by Ozymandias_117 on 2010-06-01
The bottom one.

---

### Post by fordguydude on 2010-06-01
> **Ozymandias_117 said:**
> The bottom one.

No error message now, but there are no updates available. It's been 6 days since I last installed updates. Are there really no updates available or do I need to check one on my software sources?

---

### Post by Ozymandias_117 on 2010-06-01
Post the results of ```
cat /etc/apt/sources.list
```

---

### Post by fordguydude on 2010-06-02
> **Ozymandias_117 said:**
> Post the results of ```
cat /etc/apt/sources.list
```

recommended updates work now.

But if you want to see it--

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

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

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
```

---

