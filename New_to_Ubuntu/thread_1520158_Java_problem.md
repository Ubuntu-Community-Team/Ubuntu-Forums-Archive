---
title: "Java problem"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by hesth on 2010-06-29
Hi everyone - I am having problems with Java on 10.04.

I am able to watch Youtube videos, but when I am trying another site, which I want to use for backups, it says I don't have Java installed. The Java test site says it isn't installed. 

I have tried a few suggestions from other posts, but no luck. This is a bit from the terminal if that helps?

hester@hester-laptop:~$ sudo apt-get remove openjdk-6-jre
[sudo] password for hester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-6-jre is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgmime2.4-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
hester@hester-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libgmime2.4-cil
0 upgraded, 0 newly installed, 1 to remove and 37 not upgraded.
After this operation, 254kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 144784 files and directories currently installed.)
Removing libgmime2.4-cil ...
Removing libgmime2.4-cil from Mono
hester@hester-laptop:~$ sudo apt-get remove openjdk-6-jre-headless
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-6-jre-headless is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
hester@hester-laptop:~$ sudo apt-get remove openjdk-6-jre-lib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openjdk-6-jre-lib is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
hester@hester-laptop:~$ sudo apt-get remove icedtea6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea6-plugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
hester@hester-laptop:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin
hester@hester-laptop:~$ 


Thanks

---

### Post by adit on 2010-06-29
I think you want to install java plugin for firefox
Try this
> sudo apt-get install sun-java6-plugin

---

### Post by hesth on 2010-06-29
Thanks, but it hasn't solved it. This is what I get in the terminal:

hester@hester-laptop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin

---

### Post by Miljet on 2010-06-29
Sun java is in the partner repositories. Go to System->Administration->Software Sources, Click on the Other Software tab at the top, and place a check beside the partner repository. Close the window and run the following code in the terminal.

```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
```

---

### Post by hesth on 2010-06-29
still the same error message again. Very frustrating

hester@hester-laptop:~$ sudo apt-get update
[sudo] password for hester: 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic/partner Translation-en_AU
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid Release.gpg    
Hit [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid/main Translation-en_AU
Hit [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid/restricted Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid/universe Translation-en_AU
Hit [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid/multiverse Translation-en_AU
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates Release.gpg
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-updates/main Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security Release.gpg
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-security/main Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://ftp.uni-kl.de/pub/linux/ubuntu/](http://ftp.uni-kl.de/pub/linux/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid Release         
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security Release                      
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid/multiverse Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-updates/multiverse Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) lucid-security/multiverse Sources
Reading package lists... Done
hester@hester-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
hester@hester-laptop:~$

---

### Post by nick_goodfate on 2010-06-29
can you post the contents of /etc/apt/sources.list file ?

---

### Post by Miljet on 2010-06-29
In that case, I would suggest that you try a different mirror. Go to System->Administration->Software Sources and in the center of the Ubuntu Software tab, select "Other" from the "Download From" box. Then click on "Select Best Server". Then go back and try the same commands in the terminal.

---

### Post by hesth on 2010-06-29
I just tried another mirror as suggested, but still same error:





> **nick_goodfate said:**
> can you post the contents of /etc/apt/sources.list file ?

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid multiverse
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security main restricted
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) lucid-security multiverse

---

### Post by 4chan on 2010-06-29
EDIT : **outdated**

---

### Post by howefield on 2010-06-29
You have Karmic partner enabled, you need Lucid partner for sun-java6-jre. (Or Karmic multiverse).

---

### Post by hesth on 2010-06-29
> **howefield said:**
> You have Karmic partner enabled, you need Lucid partner for sun-java6-jre. (Or Karmic multiverse).

BINGO!

I assume its because I only upgraded from Karmic instead of a fresh install that it didn't come up as the lucid partner automatically.

Although I have been using Ubuntu for a while now, I'm still a beginner!

Thanks to everyone for the help :)

---

### Post by rodrigr2006 on 2010-06-29
how did you add that repository, i started with a fresh install and i had some repositories i had to uncheck cause they were causing an error

thanks

---

### Post by howefield on 2010-06-30
> **rodrigr2006 said:**
> how did you add that repository,...

On a fresh install, you would load up System > Administration > Software Sources and click on the other software tab, place a check against partner and finish by pressing the reload button.

---

