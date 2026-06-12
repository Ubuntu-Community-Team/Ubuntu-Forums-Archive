---
title: "hi friends...i need help"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by raghub on 2011-08-23
i have just tried opening synaptic manager i got a error in ubuntu 10.04 
and also if i type any command this is the the error ........
 Malformed line 10 in source list /etc/apt/sources.list (URI parse)

---

### Post by sanderd17 on 2011-08-23
can you give us the contents of that file?

open a terminal (CTRL+ALT+T) and execute
```

cat /etc/apt/sources.list 

```

Afterwards, copy paste the contents in the forums, don't forget to use CODE tags, click on the # simbol.

---

### Post by TBABill on 2011-08-23
Try to ```
sudo gedit /etc/apt/sources.list
``` and edit the line in question. It may be a ppa or other entry that is typed incorrectly and just needs adjusted. That file is the list of sources for software for your install so each time you get updates or look for software, those are the repositories the system looks at.

---

### Post by raja.genupula on 2011-08-23
do this 
```
sudo rm -rf /var/lib/apt/lists/*
```
the do update again by using```
 sudo apt-get update
```

---

### Post by raghub on 2011-08-23
> **raja.genupula said:**
> do this 
```
sudo rm -rf /var/lib/apt/lists/*
```the do update again by using```
 sudo apt-get update
```






this is wat i get after typing first line

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.




## Major bug fix updates produced after the final release of the
## distribution.
deb India lucid-updates main restricted
deb-src India lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb India lucid universe
deb India lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb India lucid multiverse
deb India lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb India lucid-security main restricted
deb-src India lucid-security restricted main multiverse universe #Added by software-properties
deb India lucid-security universe
deb India lucid-security multiverse
deb [http://mirrors.cavecreek.net/ubuntu/](http://mirrors.cavecreek.net/ubuntu/) lucid main universe restricted multiverse
deb-src [http://mirrors.cavecreek.net/ubuntu/](http://mirrors.cavecreek.net/ubuntu/) lucid main universe restricted multiverse #Added by software-properties

---

### Post by raghub on 2011-08-23
hey this is my list.....................





deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.




## Major bug fix updates produced after the final release of the
## distribution.
deb India lucid-updates main restricted
deb-src India lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb India lucid universe
deb India lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb India lucid multiverse
deb India lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb India lucid-security main restricted
deb-src India lucid-security restricted main multiverse universe #Added by software-properties
deb India lucid-security universe
deb India lucid-security multiverse
deb [http://mirrors.cavecreek.net/ubuntu/](http://mirrors.cavecreek.net/ubuntu/) lucid main universe restricted multiverse
deb-src [http://mirrors.cavecreek.net/ubuntu/](http://mirrors.cavecreek.net/ubuntu/) lucid main universe restricted multiverse #Added by software-properties

---

### Post by raja.genupula on 2011-08-23
have you tried update  . you must go for update

---

### Post by sanderd17 on 2011-08-23
> **raja.genupula said:**
> have you tried update  . you must go for update

[s]Karmic has reached the end of life, so the update won't work.

@OP: if you want to install or update something, you need to upgrade your Ubuntu.[/s]

Sorry, what version of Ubuntu do you have? There are a lot of lines in your file that say Karmic, and others say Lucid.

---

### Post by oldos2er on 2011-08-23
"India" is not a repository, but "in.archive.ubuntu.com" is. I suggest you go here and regenerate a new sources.list: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by oldos2er on 2011-08-23
> **raja.genupula said:**
> do this 
```
sudo rm -rf /var/lib/apt/lists/*
```

What is the purpose of this? The error is in /etc/apt/sources.list.

---

### Post by sandyd on 2011-08-23
> **sanderd17 said:**
> [s]Karmic has reached the end of life, so the update won't work.

@OP: if you want to install or update something, you need to upgrade your Ubuntu.[/s]

Sorry, what version of Ubuntu do you have? There are a lot of lines in your file that say Karmic, and others say Lucid.

He/She uses Lucid.

There are ownly two karmic repos, and one is the partner repo, while the other is a commented out repo.

anyways, Im taking a guess that youve upgraded to lucid.

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo nano /etc/apt/sources.list
```Paste
```

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid universe
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://in.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://in.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://in.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://in.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb http://mirrors.cavecreek.net/ubuntu/ lucid main universe restricted multiverse
deb-src http://mirrors.cavecreek.net/ubuntu/ lucid main universe restricted multiverse #Added by software-properties

```Press Ctrl+X
```

sudo apt-get update
```

---

### Post by raghub on 2011-08-24
still i m getting the same error i tried to update malformed line 10

---

### Post by raghub on 2011-08-24
E: Lists directory /var/lib/apt/lists/partial is missing........ i m getting this now

---

### Post by raja.genupula on 2011-08-24
do this 

```
sudo mkdir /var/lib/apt/lists/partial
```

and try again

---

