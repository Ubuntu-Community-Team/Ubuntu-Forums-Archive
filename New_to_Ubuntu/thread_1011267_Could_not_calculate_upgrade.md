---
title: "Could not calculate upgrade"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by markc7 on 2008-12-14
Hi, I was wondering if someone could help me out with this.  I've finally got around to upgrading from gutsy to hardy, but it's not letting me complete the upgrade.  I get an error message saying "Could not calculate the upgrade". I've attached a screen shot.  I've done some googling and searching on this site and haven't found a solution short of doing an install from scratch, which I'd rather not do.  Any help would be greatly appreciated!

---

### Post by taurus on 2008-12-14
Do you have any third party repos in /etc/apt/sources.list?  Can you post it?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by markc7 on 2008-12-14
markc7@dell-desktop:~$ cat /etc/apt/sources.list
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) gutsy main universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) gutsy-security main universe

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
markc7@dell-desktop:~$

---

### Post by markc7 on 2008-12-14
Also, in /var/log/dist-upgrade in the file "main.log", there were two lines containing errors:

2008-12-14 16:20:23,298 ERROR Package getlibs has no priority set
2008-12-14 16:21:26,801 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

---

### Post by solwic on 2008-12-14
> **markc7 said:**
> Also, in /var/log/dist-upgrade in the file "main.log", there were two lines containing errors:

2008-12-14 16:20:23,298 ERROR Package getlibs has no priority set
2008-12-14 16:21:26,801 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

I'm not sure how to fix that, but I can say from experience that, in the end, installing fresh is much, much ***_MUCH_*** easier in the long run.  

Far simpler to backup your stuff and copy it back over than to deal with "upgrades".  

IMO, anyway.  

Good luck!

---

### Post by taurus on 2008-12-14
What happens to your /etc/apt/sources.list?  Make a backup copy of it and add these lines in there.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.orig
gksudo gedit /etc/apt/sources.list
```
Now, remove all the lines in there.  Then, add these lines to it.

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse 

```
Save it and close gedit editing window.  Now, see if you can upgrade your machine.

---

### Post by Michael.Godawski on 2008-12-14
```
michael@michael-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb http://moblock-deb.sourceforge.net/debian intrepid main
deb-src http://moblock-deb.sourceforge.net/debian intrepid main
```Just as example this is my sources.list. Yours seems to be a little short.
edit: taurus is always faster than you ....

---

### Post by markc7 on 2008-12-14
Thanks.  I did have a much longer source list but was getting error messages when I reloaded the list of updates in synaptic.  So I took out everything except what was listed there, thinking that that might have been the problem.  

taurus' advice seemed to have helped.  It's now letting me get past the "calculating upgrade" stage of the process, so I'm going to start downloading and see what happens.  

Thanks to both of you for your help!

---

