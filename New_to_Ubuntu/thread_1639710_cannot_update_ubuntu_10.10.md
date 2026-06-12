---
title: "cannot update ubuntu 10.10"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-12-07
when I try to update ubuntu through terminal i get this message: 
can anyone help??

[I]Fetched 161kB in 1min 33s (1,719B/s)                                           
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6E871C4A881574DE Launchpad PPA for Bisigi
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 4D17133CFC5D50C5 Launchpad elementaryart
W: Failed to fetch [http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release](http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
amit@amit-laptop:~$ 
[/I]

---

### Post by Hippytaff on 2010-12-07
can you post your sources list file
```

cat /etc/apt/sources.list

```
 
The last entry for lucid 10.04.

---

### Post by tajiknomi on 2010-12-07
```

```[SIZE=2]As mentioned by HIPPYTAFF , open your source.list and remove that One > [/SIZE][I] [http://www.sourceslist.eu/repo/ubunt.../lucid/Release]("http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release") [SIZE=2]because its for lucid.

Moreover try these commands 

[/SIZE][/I]```
[SIZE=4]apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update[/SIZE]

```

---

### Post by amitpokhrel on 2010-12-14
this was the output:


amit@amit-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick universe
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick multiverse
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security main restricted
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security universe
deb [http://archive.mmu.edu.my/ubuntu/](http://archive.mmu.edu.my/ubuntu/) maverick-security multiverse
deb-src [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
amit@amit-laptop:~$

---

### Post by amitpokhrel on 2010-12-14
there is nothing like: 
 [http://www.sourceslist.eu/repo/ubunt.../lucid/Release](http://www.sourceslist.eu/repo/ubunt.../lucid/Release) 
in source.list

---

### Post by amitpokhrel on 2010-12-14
now I get this message when I try to update:


Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Fetched 7,484B in 41s (181B/s)
W: Failed to fetch [http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release](http://www.sourceslist.eu/repo/ubuntu/dists/lucid/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
amit@amit-laptop:~$

---

### Post by theozzlives on 2010-12-14
Seems like you forgot the key for some of your 3rd party repos. Those last 3 can be removed from your sources.list. I ran into a similar situation a couple of times, it just means those apps won't get updated.

---

### Post by xintera. on 2010-12-14
Reconnect internet connection,or change servers -should work that way.

---

