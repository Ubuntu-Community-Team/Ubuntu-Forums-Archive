---
title: "Package Failures"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by susanpenter on 2009-06-11
I am getting an update error from my package management system, a yellow exclamation mark is appearing in the upper right system tray area and when I go to check the update status I am getting the following information.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


Please could someone advise how to deal with this I would hate to delete the wrong thing and cause further problems.

Many thanks,

Susan

---

### Post by 73ckn797 on 2009-06-11
> **susanpenter said:**
> I am getting an update error from my package management system, a yellow exclamation mark is appearing in the upper right system tray area and when I go to check the update status I am getting the following information.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/psyke83/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


Please could someone advise how to deal with this I would hate to delete the wrong thing and cause further problems.

Many thanks,

Susan

Without the "GPG" key(s) you will not be able to "fetch" or else their system is down. Probably the former.

---

### Post by susanpenter on 2009-06-11
The listings did not show these same results within the repository listsings so I deleted all the files that said they were obsolete, now I receive this message when I try and add packages in Synaptic:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by 73ckn797 on 2009-06-11
What does /etc/apt/sources.list show?

Enter in terminal:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by lindsay7 on 2009-06-11
Re: Software sources problem


type these commands in the terminal one at a time, where it says KEY, put in the key number. You should only need the last eight digits. Do this for all the key numbers listed.

gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY

gpg --export --armor KEY | sudo apt-key add -


When you are done type sudo apt-get update and then
sudo apt-get upgrade

---

### Post by susanpenter on 2009-06-12
> **73ckn797 said:**
> What does /etc/apt/sources.list show?

Enter in terminal:
```
sudo gedit /etc/apt/sources.list
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe restricted main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports universe main multiverse restricted

In answer to this question.

---

### Post by susanpenter on 2009-06-12
> **lindsay7 said:**
> Re: Software sources problem


type these commands in the terminal one at a time, where it says KEY, put in the key number. You should only need the last eight digits. Do this for all the key numbers listed.

gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY

gpg --export --armor KEY | sudo apt-key add -


When you are done type sudo apt-get update and then
sudo apt-get upgrade


gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg: WARNING: unsafe permissions on configuration file `/home/susan/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/susan/.gnupg/gpg.conf'
gpg: "KEY" not a key ID: skipping


I put the first bit of code in and hit return and it did this.  If I was meant to add a key number where do I find out what it should be?

Thanks

---

### Post by lindsay7 on 2009-06-12
>  Originally Posted by susanpenter  View Post
I am getting an update error from my package management system, a yellow exclamation mark is appearing in the upper right system tray area and when I go to check the update status I am getting the following information.

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [COLOR="Red"]A040830F7FAC5991[/COLOR]
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY[COLOR="Red"] A040830F7FAC5991[/COLOR]
W: Failed to fetch [http://packages.freecontrib.org/ubun...er/Release.gpg](http://packages.freecontrib.org/ubun...er/Release.gpg) Could not connect to packages.freecontrib.org:80 (34.52.53.34), 


>  Originally Posted by lindsay7  View Post
Re: Software sources problem


type these commands in the terminal one at a time, where it says[COLOR="Red"] KEY[/COLOR], put in the[COLOR="Red"] key number[/COLOR]. You should only need the last eight digits. Do this for all the key numbers listed.


Note, you need two key numbers at this time.

---

### Post by michy99 on 2009-06-12
> **lindsay7 said:**
> Note, you need two key numbers at this time.

Actually, they are both the same:)

---

### Post by susanpenter on 2009-06-12
I have put in the information requested and it still comes back with an error: 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys A040830F7FAC5991
gpg: WARNING: unsafe permissions on configuration file `/home/susan/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/susan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


Sorry if this should be simple :-)

---

### Post by susanpenter on 2009-06-12
The update manager has appeared again with quite a few items listed however when I click ok the error message is still coming up: 

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Theer is something I am desperate to download and install so this is becoming areal nightmare.  Any help gratefully received.

---

### Post by michy99 on 2009-06-12
What is the output of these commands?```
ls -ld /home/susan/.gnupg
ls -l /home/susan/.gnupg
```

---

### Post by susanpenter on 2009-06-13
> **michy99 said:**
> What is the output of these commands?```
ls -ld /home/susan/.gnupg
ls -l /home/susan/.gnupg
```

The first one produces this:
drwxrwxr-x 2 susan susan 4096 2009-05-12 20:51 /home/susan/.gnupg

The second one this:
total 8
-rw-rw---- 1 susan susan 28 2008-05-02 08:21 gpg.conf
-rw-rw---- 1 susan susan  0 2008-05-02 08:21 pubring.gpg
-rw-rw---- 1 susan susan  0 2008-05-02 08:21 secring.gpg
-rw-rw---- 1 susan susan 40 2008-05-02 08:21 trustdb.gpg

---

### Post by gradinaruvasile on 2009-06-13
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=856986]("http://ubuntuforums.org/showthread.php?t=856986")

---

### Post by abhiroopb on 2009-06-13
1. Restart your computer - should get rid of the lock

2. enter this into the terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991 && sudo apt-get update && sudo apt-get upgrade

---

