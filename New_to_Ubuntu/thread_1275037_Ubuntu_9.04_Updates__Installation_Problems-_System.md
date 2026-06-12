---
title: "Ubuntu 9.04 Updates  Installation Problems- System verification error"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by sarayuvijay on 2009-09-25
I am an absolute beginner in Ubuntu and just joined the community. 
During a security update session I got the following errors. 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com]("http://ae.archive.ubuntu.com/") jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release]("http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release")  

W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/...pdates/Release]("http://ae.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release")  

W: Some index files failed to download, they have been ignored, or old ones used instead. 
Could you please help me fix this.
                                                                                               __________________
                Sarayuvijay

---

### Post by philinux on 2009-09-25
Welcome aboard. 

Open a terminal, Apps>accessories>terminal

Post the output of your sources.

```
cat /etc/apt/sources.list
```

---

### Post by sarayuvijay on 2009-09-25
Thanks for your response.
This is what I got for the command
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

Just to give you the history of how I got Ubuntu.
I installed Ubuntu on my Windows XP m/c following a simple 'how to' instruction. Don't know where i went wrong but my m/c just wouldn't boot reporting a 'failed to load OS' error. Reloaded windows, got my computer going and tried installing Ubuntu again but this time on a different hard drive. Problems again and this time XP was booting and not Ubuntu. Started reading more and then fixed the boot record to point to the correct drives.  Now my machine can load with Ubuntu in one hard drive or with either Ubuntu or XP for antother hard drive. During my reading up phase read in one of the How to's that Super Grub is a must have and so down loaded it and burned the image to CD but havent installed it yet. Hope this information helps.
Thanks

---

### Post by sarayuvijay on 2009-09-27
Can somebody help on how to resolve this signature verification error. 
Thanks

---

