---
title: "Repository problems"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by susanpenter on 2009-06-24
I seem to be having problems with my repository and I think some of these may be obsolete and getting in the way please could someone advise me which I can safely delete.

I have enclosed a screen shot.

Many thanks

Susan

---

### Post by nothingspecial on 2009-06-24
If you`ve upgraded to jaunty you shouldn`t need the gutsy repos, allthough they look like they`ve been disabled.

What problems are you having?

Did you upgrade from Gutsy straight to Jaunty as this is not recommended?

---

### Post by tarps87 on 2009-06-24
Assuming you have updated to Jaunty you can disable/un-check the Gusty entries. Could you post the out put of your sources list so we can have a more detailed look at the rest
```
gedit /etc/apt/sources.list
```
(Can you wrap the contexts in [code] tags when posting it, the # button on the toolbar)
Thanks

---

### Post by susanpenter on 2009-06-24
> **tarps87 said:**
> Assuming you have updated to Jaunty you can disable/un-check the Gusty entries. Could you post the out put of your sources list so we can have a more detailed look at the rest
```
gedit /ect/apt/sources.list
```
(Can you wrap the contexts in [code] tags when posting it, the # button on the toolbar)
Thanks

something very strange is going on when I put this code in the notebook page opened but it was blank!

---

### Post by halitech on 2009-06-24
easier way is
```
cat /etc/apt/sources.list
```since we just want to look at them for now

---

### Post by susanpenter on 2009-06-24
Now I have a result
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe restricted main
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports universe main multiverse restricted
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) jaunty main
#

```

---

### Post by halitech on 2009-06-24
you can delete this
```
## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```
and this```
## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```
and this
```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```
change gutsy to jaunty in this
```
deb-src http://archive.canonical.com/ubuntu gutsy partner
```

---

### Post by mgmiller on 2009-06-24
If you are running Jaunty, there should not be any lines referring back to the older gutsy entries.  

There are other problems here as well.  All the jaunty entries are from "archive" reposiltories.  This is not right either.  The partner repositories are from archive, but the main ones should not be.

How did you upgrade this install?  It looks like you may have tried to go straight from gutsy to Jaunty.  This is not recommended.  You need to upgrade to each new release in turn.

What you can do is try running System > Administration > Software sources.
Go to the Third-party Software tab and on the top 3 lines that mention Gutsy/ 7.10 click to high light and then click remove at the bottom of the screen.   The next ones that say unsupported can be unchecked.  You can look at those later. For the remaining ones there, click it to select it and then click to edit it.  On the distribution line, make sure it says Jaunty, then click OK.

Next, go to the Ubuntu software tab and make sure that at least the first 4 choices are checked.  Source code is optional, unless you need it.

Beneath that is the "dowload from" drop down.  Open that and select "other".
In the resulting dialog, click "Select Best Server".  It will take a bit, but when it's done you click the close button.   It will tell you the "Information about available software is out of date" and will suggest you reload.  Press the reload button and wait for it to finish.  When it is done, the program will exit itself.  Do not get impatient and close the window yourself, wait for it to close.


If you are still having problems at that point, repost here with the new sources.list and we can try going through it line by line.

---

### Post by susanpenter on 2009-06-24
> **mgmiller said:**
> 
How did you upgrade this install?  It looks like you may have tried to go straight from gutsy to Jaunty.  This is not recommended.  You need to upgrade to each new release in turn.


I did do this, when the icon appears to upgrade I allow it so I've had Ibex (was that the name? ) in between.

I will follow your guide above thanks,

---

### Post by tarps87 on 2009-06-25
> **susanpenter said:**
> something very strange is going on when I put this code in the notebook page opened but it was blank!

Sorry mistyped it:

ect should have been etc

gedit /etc/apt/sources.list

It looks like it is sorted now

Yes it the one in-between was called Ibex (still is :))

---

