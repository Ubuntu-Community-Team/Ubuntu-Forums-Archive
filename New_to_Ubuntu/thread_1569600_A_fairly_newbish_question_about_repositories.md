---
title: "A fairly newbish question about repositories"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by juil on 2010-09-07
I've done some reading but still a newb...
When I upgraded to Lucid 10.04, the repository list changed and my software sources windows looks like the picture attached.

I would like to know what I should remove from the software sources window?
Also if someone can explain the relation between the software sources window and sources.list.

In the pic, the 'unsupported updates' URI is [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/). 

I'm guessing all of these were disabled because i'm using the waterloo URI and whatever is from archive.ubuntu has been updated to lucid. I'm assuming it's safe to remove the first five in the list (up to karmic), but what about 'disabled on upgrade to lucid' ones? Also I can't remember where I got the Medibuntu repository from. I've already asked about the relation between sources.list and software sources but arent they supposed to reflect each other? Thanks in advance.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-updates main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid universe
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid multiverse
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-security main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-security universe
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ lucid-security multiverse
# deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/dockbar-main/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/docky-core/ppa/ubuntu lucid main # disabled on upgrade to lucid

#FILE: /etc/apt/sources.list
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

Also on a somewhat different topic and also very noob question. My ALT+F2 doesn't open up the RUN window. How can i enable it?

---

### Post by plucky on 2010-09-07
You can remove all the ones that doesn't have Lucid in the line except, I would edit the "Partner" repository line and change Karmic to Lucid and then tick the boxes.

For medibuntu go [Here](https://help.ubuntu.com/community/Medibuntu) and add the Medibuntu Lucid repository.

Remove the Hardy PPA as well.

Or 

Go [Here](http://repogen.simplylinux.ch/) and generate a new Sources.list.

All the repositories in Software Sources have a # in front of them in the sources.list which disables them.That is why they are not ticked.If you remove them from Software Sources,they will be removed from sources.list.

You can also get other repositories in the directory /etc/apt/sources.list.d which will show up in Software Sources e.g Medibuntu.

From a terminal ```
ls -l /etc/apt/sources.list.d
``` and see what is in there.

> Also on a somewhat different topic and also very noob question. My ALT+F2 doesn't open up the RUN window. How can i enable it? 


See what is setup in **System > Preferences > Keyboard Shortcuts**


Good Luck

---

### Post by juil on 2010-09-07
Thanks for replying! The sources.list generator is pretty awesome. I followed the instructions to add medibuntu, and it seemed to work but I'm still confused because it doesn't reflect in the sources.list as you can see. The Software Sources has Medibuntu selected but it doesn't show in the sources.list.

Oh also I have a microsoft keyboard so when ALT is pressed the F2 becomes and UNDO key. So it's ALT+UNDO now. :P

---

### Post by plucky on 2010-09-07
> **juil said:**
> Thanks for replying! The sources.list generator is pretty awesome. I followed the instructions to add medibuntu, and it seemed to work but I'm still confused because it doesn't reflect in the sources.list as you can see. The Software Sources has Medibuntu selected but it doesn't show in the sources.list.

Oh also I have a microsoft keyboard so when ALT is pressed the F2 becomes and UNDO key. So it's ALT+UNDO now. :P

Medibuntu is located in ```
/etc/apt/sources.list.d/medibuntu.list
``` note the .d added to sources.list to make it a sub-directory

Try ```
ls -l /etc/apt/sources.list.d
``` from a terminal.

This is where other repositories that are not run by Canonical should be placed.e.g PPA's


Good Luck

---

