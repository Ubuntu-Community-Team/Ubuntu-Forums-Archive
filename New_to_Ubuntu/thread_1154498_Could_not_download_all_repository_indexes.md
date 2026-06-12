---
title: "Could not download all repository indexes"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by fishmanstyles on 2009-05-09
Hiya, basically i'm trying to download Azureus using the Add/Remove applications, because i got sooo lost trying to follow the online instructions with command lines etc....

so yeah, i got a couple errors and tried adding # to the sources list as detailed on a similar thread.. .and it's managed to reduce it to only 1 error now:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]]("http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:")

Below is the sources list, everything has # by it? is there sometning i'm not doing here?
any help would be much appreciated, and i'm only posting in the Absolute Beginner talk, because i couldn't find the 'Complete Absolute and rather inept Beginner talk' section :confused:

user@ubuntu:~$  cat /etc/apt/sources.list
# deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty main restricted
# deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-updates main restricted
# deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty universe
# Line commented out by installer because it failed to verify:
#deb-src [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-backports main restricted universe multiverse
# deb-src [http://192.168.10.14:8022/ubuntu](http://192.168.10.14:8022/ubuntu) feisty-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
user@ubuntu:~$

---

### Post by dLeon on 2009-05-09
The only not right about your source.list is the all the repository address has # in front of it. Of course you won't catch anything. I see you already notice that too.

Get rid # in front of text start with deb. You can include 'deb-src' if you want.

Note; don't yet enable the one with 'backport' if you don't understand this all game yet.

Err... feisty is Ubuntu LTS, right? I don't remember every single Ubuntu codenames.

---

### Post by -kg- on 2009-05-09
> **dLeon said:**
> The only not right about your source.list is the all the repository address has # in front of it. Of course you won't catch anything. I see you already notice that too.

Get rid # in front of text start with deb. You can include 'deb-src' if you want.

Note; don't yet enable the one with 'backport' if you don't understand this all game yet.

Err... feisty is Ubuntu LTS, right? I don't remember every single Ubuntu codenames.

No, I don't believe Feisty was LTS, and nevertheless, it's [support ended on Oct 19, 2008,]("http://ubuntuforums.org/showthread.php?t=947232") so it will no longer be supported by the normal means.  That is likely why you no longer have access to the repositories.

Your best bet is to go through the upgrade process, or to fresh install Hardy 8.04 (which *is* an LTS version and supported until 2011) or to Intrepid or Jaunty, which are the most recent non-LTS versions.

Considering that the next upgrade step from you (Gutsy) is already out of support itself, probably your best bet would be a clean install of one of the more recent Ubuntu Distros...of course, after backing up your critical data to another location.

---

### Post by dLeon on 2009-05-10
I C... So he has an old version. [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

'-kg-' is right 'fishmanstyles', you should; if not must upgrade to the new version.

---

