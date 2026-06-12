---
title: "Update Issues, Software Sources Lucid 10.04"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by midnightferret on 2011-02-06
Hi, I've been getting errors when I try to update, and they look like this:

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/dists/hoary-extras/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/dists/hoary-extras/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/dists/hoary-extras/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

So, I searched around, I tried to fix is myself (sad, I know). My apt sources.list looks like:

```
cbelsom@Davros:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
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
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://us.archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb http://download.videolan.org/pub/videolan/debian sarge main
deb-src http://download.videolan.org/pub/videolan/debian sarge main
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/ hoary-extras main universe multiverse restricted
cbelsom@Davros:~$ 

```

Can you help? I edited the update sources in the GUI. Can you help me "unfix" my problems, and fix them correctly? A little knowledge is a dangerous thing...

---

### Post by Paqman on 2011-02-06
Whoa, Hoary! Ubuntu 5.04 (Hoary Hedgehog) is so-called because it came out in April 2005!

The repos for Hoary have been closed since 2006, so you'll want to delete all references to it from your software sources.

---

### Post by midnightferret on 2011-02-06
Whoops. I just thought that meant "hoary" as in "old updates." I was having troubles, and found those sources on the forums. That should I replace them with?

---

### Post by snowpine on 2011-02-06
Delete all lines that reference "hoary" or "debian". Use only repositories that are specifically designed for Ubuntu 10.04 Lucid Lynx. Don't follow random tutorials you read on the internet unless you trust the author and are confident they are specific to your release.

---

### Post by Paqman on 2011-02-06
> **midnightferret said:**
> What should I replace them with?

Nothing. If you really want to enable the Backports repo for your own version, just check the button on the first tab of the Software Sources tool. It won't do much though, Backports is designed to get important updates into old versions, and your version isn't old.

But yes, get rid of the Debian repos too. Good spot snowpine!

---

### Post by midnightferret on 2011-02-06
Will I lose updates for vlc and skype?

---

### Post by uRock on 2011-02-06
> **midnightferret said:**
> Will I lose updates for vlc and skype?
No.

---

### Post by Paqman on 2011-02-06
> **midnightferret said:**
> Will I lose updates for vlc and skype?

VLC is in the Universe repo, and Skype is (IIRC) in the Partner repo. If you have both of those enabled, you'll get updates. It's always best to get your software from the official Ubuntu repos, instead of adding 3rd party sources. 

Obviously some stuff you can only get from external sources, like the stuff in the Google repo that you've got enabled. Keep that one.

---

### Post by midnightferret on 2011-02-06
Rock n' roll! If the following looks ok, and I don't get any errors on the update manager for a couple days/restarts, I'll mark the whole thing solved. Thanks, guys!

```
cbelsom@Davros:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
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
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://us.archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
cbelsom@Davros:~$ 

```

---

### Post by snowpine on 2011-02-06
Looks good to me. :)

---

