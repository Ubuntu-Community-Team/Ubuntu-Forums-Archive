---
title: "Synaptic Package Manager Won't Open!"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by erinhg on 2011-08-08
**Newbie to the forum but was wondering if anyone could help. every time I go to open synaptic package manager I get the following error message **


E: Type ‘--2011-08-08’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

**I tried this solution:**
sudo rm /var/cache/apt/*.bin
**followed by:**
sudo aptitude install synaptic
This gave me a similar error message. 

**so I did this:**
 gksudo gedit /etc/apt/sources.list
**and added a # to line 1? I'm not sure if this was the correct thing to do. This is quite possibly where I've gone wrong but I'm new and don't have a clue! Anyway, I did so and saved and then run synaptic. Shut it down and then entered **
code: sudo apt-get update
sudo apt-get upgrade

**I then got:**
E: Type ‘--2011-08-08’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Type ‘--2011-08-08’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
E: The package lists or status file could not be parsed or opened.


**my (/etc/apt)saaaays:** 
## deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse



**sorry if there's a lot of unnecessary information in this post. It's taking me a while to get used to all this. Any help would be much appreciated! Thank you!**
ohh and I'm running ubuntu 10.10 maverick meerkat

---

### Post by arochester on 2011-08-08
Notice the difference?

(source list) /etc/apt/sources.list.d/medibuntu.list

(gksudo gedit) /etc/apt/sources.list

Try...gksudo gedit /etc/apt/sources.list.d/medibuntu.list

---

### Post by erinhg on 2011-08-09
> **arochester said:**
> Notice the difference?

(source list) /etc/apt/sources.list.d/medibuntu.list

(gksudo gedit) /etc/apt/sources.list

Try...gksudo gedit /etc/apt/sources.list.d/medibuntu.list

**Ahhh I see where I went wrong. Thanks for your help arochester, anyway, now the sources.list.d.medibuntu.list(etc/apt) is completely empty!!**

**Now synaptic is showing this error message:**


E: Type ‘Resolving’ is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

**any suggestions?**

---

### Post by Elfy on 2011-08-09
IT appears that the medibuntu list is seriously wrong, it's likely to be quicker to delete it ans redo the necessary steps to restore it from a terminal
```

sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

As far as I am aware any of the lines in any of the sources lists should have either

deb
deb-source
# 

at the beginning of them - anything else will cause failures.

Edit - it's likely that the error in the last post was caused byt not running an update - either sudo apt-get update or reload from one of the GUI's. You can edit all the sources files - but until they are updated then the system still thinks they are as they were originally.

---

### Post by westie457 on 2011-08-09
There is a command that will remove the problems. I think it looks something like this ```
rm /etc/apt/sources.list.d/*
```

DO NOT RUN THIS COMMAND WITHOUT GETTING CONFIRMATION THAT IT IS RIGHT.
If I have got that command wrong and it is run then there could be serious consequences to your system. IE totally borked.

Then run ```
sudo apt-get update
sudo apt-get upgrade
```

It is really not a good idea to manually edit your sources list.
Far better to do it through Synaptic > Settings > Repositories.

---

### Post by westie457 on 2011-08-09
> **forestpiskie said:**
> IT appears that the medibuntu list is seriously wrong, it's likely to be quicker to delete it ans redo the necessary steps to restore it from a terminal
```

sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

As far as I am aware any of the lines in any of the sources lists should have either

deb
deb-source
# 

at the beginning of them - anything else will cause failures.

Edit - it's likely that the error in the last post was caused byt not running an update - either sudo apt-get update or reload from one of the GUI's. You can edit all the sources files - but until they are updated then the system still thinks they are as they were originally.

+1 

You posted while I was typing so did not see your reply until after.
And yes I very nearly got my version of the command right. Very glad you got in before me.

---

### Post by erinhg on 2011-08-09
**ahh wow thank you so much everyone for the help. forestpiskie you did the job, it's all fixed now! thanksssss :)**

---

