---
title: "updates not authenticated"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by candtalan on 2010-08-06
Normal  unr 10.04 with medibuntu, I have had no problems with updates previously.

When attempting to do an update now I am getting a warning

 
You are about to install software that cannot be authenticated! (etc etc)


Details show that the list includes the following, not a complete list though:

========================================
apt (version 0.7.25.3ubuntu9) will be upgraded to version 0.7.25.3ubuntu9.1
apt-transport-https (version 0.7.25.3ubuntu9) will be upgraded to version 0.7.25.3ubuntu9.1
apt-utils (version 0.7.25.3ubuntu9) will be upgraded to version 0.7.25.3ubuntu9.1
base-files (version 5.0.0ubuntu20) will be upgraded to version 5.0.0ubuntu20.10.04.1
firefox (version 3.6.6+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-branding (version 3.6.6+nobinonly-0ubuntu0.10.04.1) will be upgraded to version 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-gnome-support (version 3.6.6+nobinonly-0ubuntu0.

========================================

Am I being unusually sceptical in thinking that the problem does not lie in the software, but in the update process or at the software sources? (Server for uk?)

my machine needs 31 packages for updates. another machine needs only two  - a straight ubuntu 10.04, and it now complains of the same problem.

And no, I don't install  anything unusual, I am a careful ubuntu pointy clicky end user only

help please?

---

### Post by Tiberion on 2010-08-06
i am guessing here but it could be the firefox upgrades.  I am in the US and have not experienced that issue.

---

### Post by lovinglinux on 2010-08-06
Did you add any PPA repository to your sources list?

---

### Post by Tiberion on 2010-08-06
I have in the past and didn't have any issues

---

### Post by candtalan on 2010-08-06
> **lovinglinux said:**
> Did you add any PPA repository to your sources list?

where is my sources list located please I can post a copy of the list?

---

### Post by JC Cheloven on 2010-08-06
> **candtalan said:**
> where is my sources list located please I can post a copy of the list?

/etc/apt/sources.list

---

### Post by candtalan on 2010-08-06
> **JC Cheloven said:**
> /etc/apt/sources.list

pasted:




#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse



anything here look wrong?

---

### Post by candtalan on 2010-08-06
fwiw my other machine with normal ubuntu needs only two updates:



libmysqlclient16 (version 5.1.41-3ubuntu12.3) will be upgraded to version 5.1.41-3ubuntu12.6
mysql-common (version 5.1.41-3ubuntu12.3) will be upgraded to version 5.1.41-3ubuntu12.6

and this is also warning about lack of authentication

---

### Post by candtalan on 2010-08-06
> **candtalan said:**
> fwiw my other machine with normal ubuntu needs only two updates:
libmysqlclient16 (version 5.1.41-3ubuntu12.3) will be upgraded to version 5.1.41-3ubuntu12.6
mysql-common (version 5.1.41-3ubuntu12.3) will be upgraded to version 5.1.41-3ubuntu12.6
and this is also warning about lack of authentication

Ah. I changed the software sources entry from UK server to Main server and this machine updated normally without any warning messages. I conclude it is related to th eUK update server, presumably something to do with authentication?

Also, I have now done the same thing on the first machine (UNR) and the authentication failure warning has, again, gone.

I am marking this thread solved, because I can complete updates. However there remains an apparent current problem  with UK server for updates I think.

---

### Post by JC Cheloven on 2010-08-06
> **candtalan said:**
> Ah. I changed the software sources entry from UK server to Main server and this machine updated normally without any warning messages. I conclude it is related to th eUK update server, presumably something to do with authentication?
Also, I have now done the same thing on the first machine (UNR) and the authentication failure warning has, again, gone.
I am marking this thread solved, because I can complete updates. However there remains an apparent current problem  with UK server for updates I think.
Glad you solved it (well, kind of :) ). I was about suggesting you to change the mirror. 
There is nothing weird in your sources.list though.

---

