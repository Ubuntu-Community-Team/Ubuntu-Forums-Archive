---
title: "E:Unable to Locate Package"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by dienamicz on 2011-04-25
Hey all, im completee beginner.. I've seen othern threads regarding this problem but mine is consistent. 

when trying to install openssh  i get the following message :

 "E:Unable to Locate Package" 

AND

 when trying to install vsftpd i get the following:
"
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I have done the following:

System > Administration > Synaptic Package Manager

Click on "Reload" and check whether you get the same issue after that or not

but i still get the same message.

The output of : sudo apt-get updadate is:

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg              	 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                       	 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en         	 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick Release.gpg           	 
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources   	 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources              	 
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages        	 
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick Release
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates Release
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/main Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/restricted Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/universe Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://pe.archive.ubuntu.com](http://pe.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done

Also the output of cat /etc/apt/sources.list is

> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse


Hopefully you guys can send me in the right direction. Thank you


pedro

---

### Post by K_45 on 2011-04-25
```
sudo apt-get install openssh-client openssh-server
```

---

### Post by sikander3786 on 2011-04-25
Welcome to the forums :-)

The package is named 'openssh-server' so the proper command would be

```
sudo apt-get install openssh-server
```

For other related packages,

[http://packages.ubuntu.com/search?keywords=openssh&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=openssh&searchon=names&suite=maverick&section=all)

---

### Post by antony.s on 2011-04-25
(because openssh is not a package name)

In future, you can search for packages with

```
apt-cache search *name*
```

---

### Post by 3rdalbum on 2011-04-25
> **dienamicz said:**
> 
 when trying to install vsftpd i get the following:
"
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

You can only have one package manager working at a time. If you're already running apt-get somewhere else, or have Synaptic open, or are doing something in Update Manager or Software Center, then you will get this message if you try to install software while another package manager is working.

---

### Post by dienamicz on 2011-04-25
Thank you very much for your answers..  how can i verify that it was correctly installed?

---

### Post by K_45 on 2011-04-25
Run the program and test it out, either from the terminal or from the menu.

---

