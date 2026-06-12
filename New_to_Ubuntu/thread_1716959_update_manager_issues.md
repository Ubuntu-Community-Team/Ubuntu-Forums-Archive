---
title: "update manager issues"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by wizz180 on 2011-03-29
hi there 

i am having problems with my update manager, my ubuntu software centre and my synaptic package manager can any one help me please?


when i open my update manager i get this message pop up:
An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘my password’ is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

with the synaptic manager i get:
E: Type ‘my password’ is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

and i think this is linked with the software centre because it shows no shows no software or any installed programs.

does anyone know what this may mean i am new to ubuntu and i am using Ubuntu 10.04.1 Lucid Linux.
If anyone can help this would mean alot to me thanks for your time.
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by ~Plue on 2011-03-29
seems like a malformed line in your sources.list
post the output of the following from a terminal (applications>accessories)
```
cat /etc/apt/sources.list
```

---

### Post by wizz180 on 2011-03-29
thanks i have done that what do i do now thank you for the quick reply sorry to be a pain lol

this is what came up:

billy@ubuntu-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
my password



wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-
sudo apt-key add -
sudo apt-get update

ndnc

dab

vv
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-
sudo apt-key add -

---

### Post by ~Plue on 2011-03-29
run *```
gksu gedit /etc/apt/sources.list
```*delete the following lines and save the file (they aren't valid repository lines)

> 
[COLOR=Red]my password

wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-[/COLOR] [COLOR=Red]
sudo apt-key add -
sudo apt-get update

ndnc[/COLOR] [COLOR=Red]

dab[/COLOR] [COLOR=Red]

vv[/COLOR] [COLOR=Red]
wget [http://packages.dfreer.org/7572013D.gpg](http://packages.dfreer.org/7572013D.gpg) -O-
sudo apt-key add -[/COLOR]
the  run ```
*sudo apt-get update*
```

---

### Post by wizz180 on 2011-03-29
i solved the problem however i still got the error sign on my task bar and when i click it it comes up with the now working synaptic package manager u must hate right now lol thanks for everythin

---

### Post by ~Plue on 2011-03-29
no worries :) 
after all, this *is* a support forum

---

