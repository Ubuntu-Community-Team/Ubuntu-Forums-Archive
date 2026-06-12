---
title: "Can't find packages (Server 8.10)"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by BUNAC on 2008-12-16
Hello,
Can someone help me please as I'm about to give up with linux :confused:

I've just decided to install Server 8.10 as I was getting nowhere with 8.04 so thought I'd take a deep breath and start again!!

I've got to the command prompt and I'm trying to install the packages I need but everytime I get the message "E: Couldn't find package ....."

I can ping the outside world (e.g. [www.google.co.uk](www.google.co.uk)).

Where do I go from here?
Apologies for being a complete noob and thanks in advance for your help!!

Cheers
Tom

---

### Post by Tatty on 2008-12-16
Have you downloaded the package lists?
```
sudo apt-get update
```

check if a package exists with

```
apt-cache search <package name>
```

What are you trying to install?

---

### Post by bumanie on 2008-12-16
You probably haven't enabled your software sources yet. (Assuming you have a GUI) Go to System --> Administration --> Software sources and check the first 4 boxes and ensure the cd-rom box is unchecked. Then go to third party software and check the boxes there. After that you should be able to download stuff.
If you have no GUI, here's a copy of my /etc/apt/sources list. You can cut and paste it to yours by > gksudo gedit /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20081001)]/ intrepid main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid main restricted 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates main restricted 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid universe 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid universe 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates universe 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid multiverse 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid multiverse 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates multiverse 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner 

deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security main restricted 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security main restricted 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security universe 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security universe 
deb [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security multiverse 
deb-src [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) intrepid-security multiverse 

Hope that helps.

---

### Post by BUNAC on 2008-12-17
Don't know what I was doing yesterday but today it works!!

Thanks for your help guys.
):P

---

