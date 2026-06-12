---
title: "cannot install packages, tried several ways, 404 error"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by waz668 on 2010-10-28
I've tried installing mp3splt and audacity using apt-get and synaptic

All ways give me a message like 

"Failed to fetch  [http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity-data_1.3.9~beta1-1~getdeb1_all.deb]("http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity-data_1.3.9%7Ebeta1-1%7Egetdeb1_all.deb")   404 Not Found"

for example:

wazza@wazza-laptop:~$ sudo apt-get install audacity
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaudclient1 libmowgli1 libmcs1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  audacity-data
Suggested packages:
  ladspa-plugin
The following NEW packages will be installed:
  audacity
The following packages will be upgraded:
  audacity-data
1 upgraded, 1 newly installed, 0 to remove and 222 not upgraded.
Need to get 4916kB of archives.
After this operation, 8507kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  audacity-data audacity
Install these packages without verification [y/N]? y
Err [http://getdeb.masio.com.mx](http://getdeb.masio.com.mx) jaunty/ audacity-data 1.3.9~beta1-1~getdeb1
  404 Not Found
Err [http://getdeb.masio.com.mx](http://getdeb.masio.com.mx) jaunty/ audacity 1.3.9~beta1-1~getdeb1
  404 Not Found
Failed to fetch [http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity-data_1.3.9~beta1-1~getdeb1_all.deb]("http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity-data_1.3.9%7Ebeta1-1%7Egetdeb1_all.deb")  404 Not Found
Failed to fetch [http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity_1.3.9~beta1-1~getdeb1_amd64.deb]("http://getdeb.masio.com.mx/getdeb/ubuntu/jaunty/au/audacity_1.3.9%7Ebeta1-1%7Egetdeb1_amd64.deb")  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

any suggestions?

---

### Post by waz668 on 2010-10-29
?

---

### Post by arochester on 2010-10-29
There may be a mistake in your sources list. Open a Terminal and issue the command: kdesudo gedit /etc/apt/sources.list

Copy and paste the result here

---

### Post by migs73 on 2010-10-29
> **arochester said:**
> There may be a mistake in your sources list. Open a Terminal and issue the command: gksudo gedit /etc/apt/sources.list

Copy and paste the result here

+1 the web pages not found do not exist but the files you are needing do. The web address does not require 'getdeb/ubuntu' in the middle.

---

### Post by waz668 on 2010-10-29
content of sources.list:

# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

---

### Post by waz668 on 2010-10-29
> **migs73 said:**
> +1 the web pages not found do not exist but the files you are needing do. The web address does not require 'getdeb/ubuntu' in the middle.
thanks, what can I do about it?

---

### Post by waz668 on 2010-10-29
any suggestions?

---

### Post by oldfred on 2010-10-29
Are you still running 9.04 Jaunty? Your distro says 9.10 Karmic?

Your sources list is all Jaunty.

---

### Post by xumuk37 on 2010-10-29
probably you've got some invalid ppa... try to look for it in /etc/apt/sources.list.d with the name something like url you've posted before...

---

### Post by waz668 on 2010-10-30
installed Karmic 9.10, thank you for the help!

---

