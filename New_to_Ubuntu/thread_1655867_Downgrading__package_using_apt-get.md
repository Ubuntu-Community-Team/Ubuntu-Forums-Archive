---
title: "Downgrading  package using apt-get"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by ps_sach on 2010-12-30
Dear all,
         I want to downgrade php from 5.3.3 to 5.3.2 using apt-get, but couldn't do it.


Any help will be appriciated!


Thanks in adv.

---

### Post by Brandon Williams on 2010-12-31
```
sudo apt-get install packagename=version
```

for example, on my 10.10 system, this:

```
sudo apt-get install software-center=3.0.4
```

will downgrade software-center from the currently installed version (3.0.7) to version 3.0.4.

---

### Post by Brandon Williams on 2010-12-31
oops, double-posted.

---

### Post by ps_sach on 2011-01-27
Thank you Brandon  for the reply!

I am trying to install as  - 
[HTML]
sudo apt-get install php5=5.3.3
[/HTML]

but getting error - 

[HTML]E: Version '5.3.3' for 'php5' was not found[/HTML]


Thanks again !!
ps_sach

---

### Post by ps_sach on 2011-01-27
Hi again, 
I wanted to install 5.3.3, so this solution for this perticular php version.

I purged existing php5, libapache2-mod-php5,php5-cli, php5-common. 
I replaced the contents of /etc/apt/sources.list by 

[HTML]
# 
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://bd.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bd.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick universe
deb http://bd.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bd.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://bd.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://bd.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://bd.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
[/HTML]

Then I updated the apt-get repositories by - 
[HTML]
apt-get update
[/HTML]

Then install php5 using apt-get, you should get php5.3.3.
[HTML]
apt-get install php5 ibapache2-mod-php5 php5-cli php5-common
[/HTML]

Cheers!!!
ps_sach.

---

