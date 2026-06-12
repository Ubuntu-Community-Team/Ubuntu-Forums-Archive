---
title: "&quot;hit&quot; &quot;err&quot; &quot;ign&quot; in system updates"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Legeril on 2011-06-29
I currently have the red "!" of update information outdated and I can't get rid of it, when I 'sudo apt-get update' I get quite a few "Ign" (ignore?) and the update errors on "http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz". 

Could this be causing it? And how would I go about fixing this? Is this package important?

Thank you :(

---

### Post by JC Cheloven on 2011-06-29
AFAIK murrine is only a gtk theme for your desktop. It seems you have told your system at some point to update that from a PPA (kinda extraofficial repository). I wouldn't care that much, it will probably be due to some temporal unavailability of the ppa that will fix be fixed soon.

Nevertheless, please post back the output of this at terminal (it's basically your repositories) as it can help to see whether something strange is in or not.
```
cat /etc/apt/sources.list
```

Regards

---

### Post by Legeril on 2011-06-30
```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cn.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cn.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://cn.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid universe
deb http://cn.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cn.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://cn.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

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
deb http://cn.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

here you go, I went to edit sources.list but the link throwing up the error isn't in there..

---

### Post by mcduck on 2011-06-30
> **Legeril said:**
> I currently have the red "!" of update information outdated and I can't get rid of it, when I 'sudo apt-get update' I get quite a few "Ign" (ignore?) and the update errors on "http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz". 

Could this be causing it? And how would I go about fixing this? Is this package important?

Thank you :(

Have you tried what happens if you actually start installing updates?

("*apt-get update*" updates the information about available packages and their version, while "*apt-get upgrade*" is the command that actually downloads and installs the updated packages.)

Anyway, the murrine-daily PPA repository doesn't seem to exist any more so you could remove that from your software sources. You can do that either through Synaptic Package Manager, or the Ubuntu Software Center, or by removing manually the sources.list file for that PPA from /etc/apt/sources.list.d/. (The file is probably called something like "murrine-daily-ppa-lucid.list")

---

### Post by CaptainMark on 2011-06-30
the 'ign' is normal dont worry about that one, it just means apt-get has checked the 'table of contents' (of a kind) and found nothing has changed so doesnt scan the rest of the repository

---

### Post by zer010 on 2011-06-30
> **mcduck said:**
> Have you tried what happens if you actually start installing updates?

("*apt-get update*" updates the information about available packages and their version, while "*apt-get upgrade*" is the command that actually downloads and installs the updated packages.)

Was my first thought as well...
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by alphacrucis2 on 2011-06-30
Have a look under /etc/apt/sources.list.d/

You may find that the ppa has its own <whatever>.list file in there. If so you can comment out the lines or else just disable the ppa via synaptic

---

### Post by Legeril on 2011-06-30
done and done, just went here /etc/apt/sources.list.d/ and deleted the ppa and save file..

Things seems fine now

---

