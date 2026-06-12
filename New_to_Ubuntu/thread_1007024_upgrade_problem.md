---
title: "upgrade problem"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by catdog44 on 2008-12-10
I am running 7.4 feisty but I can't upgrade to 7.1 to get 8.4. I keep getting an error message that says:

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]

Another page on the ubuntu site suggested that I add these lines to my /etc/apt/sources.list file

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

I did this and still got the same error.  I really don't want to do a clean/fresh install so is there something I can do.

Also here is my source list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

## Clemson Ubuntu Repository
deb [http://archive.clemsonlinux.org/](http://archive.clemsonlinux.org/) feisty main restricted

##Added to be able to update feisty
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

---

### Post by zzHanks on 2008-12-10
Try this [http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy](http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy)

I didn't find an how to for Hardy.

---

### Post by LowSky on 2008-12-10
According to this: [http://ubuntuforums.org/showthread.php?t=947232](http://ubuntuforums.org/showthread.php?t=947232)

Fiesty's servers went down in October. To upgrade now, you will need to download a new LiveCD I recommend using 8.04 and not 8.10  because it will be active much longer (3 years apposed to 18 months)

---

