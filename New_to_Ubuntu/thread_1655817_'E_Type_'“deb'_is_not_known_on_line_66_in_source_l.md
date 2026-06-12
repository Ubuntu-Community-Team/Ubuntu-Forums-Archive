---
title: "'E Type '“deb' is not known on line 66 in source list /etc/apt/sources.list':"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by fmlyrnn on 2010-12-30
Many failed attempts at Installing and running burg-manager. Here is the error message when trying to update:
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) maverick main
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
deb-src [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
“deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free”
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main  non-free
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free

---

### Post by Verbeck on 2010-12-30
from a terminal, run [I]
```

gksu gedit /etc/apt/sources.list
```[/I]
delete the 66th line and save the file
```

[COLOR=Red]&#8220;deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu)  lucid main non-free&#8221;[/COLOR]
```after that, run *sudo apt-get update*

---

### Post by fmlyrnn on 2010-12-30
Thank you for the "speedy" reply! I will attempt this resolution and get back to the Forum and you with the results.

---

### Post by fmlyrnn on 2010-12-30
> **Verbeck said:**
> from a terminal, run [I]
```

gksu gedit /etc/apt/sources.list
```[/I]
delete the 66th line and save the file
```

[COLOR=Red]“deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu)  lucid main non-free”[/COLOR]
```after that, run *sudo apt-get update*


Excellent! Now, with your help I have a working Ubuntu Software Center back. I thank you! Meanwhile, is there a clear-cut way of Installing burg-manager? I already have BUC Installed but when I try to Install burg-manager I get the icon in Applications>System Tools, once clicked on I get the Prompt for root Password, which I enter and nothing happens...

---

### Post by QLee on 2010-12-30
[QUOTE=fmlyrnn]...

deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
deb-src [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free
“deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free”
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main  non-free
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) lucid main non-free[/QUOTE]


If this is a Maverick install, there shouldn't be any need for the last 5 lines. I would just delete them all if it was my system.

---

### Post by fmlyrnn on 2010-12-30
> **QLee said:**
> If this is a Maverick install, there shouldn't be any need for the last 5 lines. I would just delete them all if it was my system.

Thank you for your "speedy" reply! I now have burg-manager Installed on Ubuntu 10.10, and this would not have happened without you and this wonderful Forum! However, I had Deleted just the one line as suggested in Verbeck's earlier reply to this query, and still there is no Splash Screen. The Option Parameters / Basic / Select default OS to Boot  has nothing in the Drop-Down, and in Parameters / Advanced Parameters I am lost but I do see "quiet splash". Nothing happens when I click Change.

---

### Post by QLee on 2010-12-31
[QUOTE=fmlyrnn]...However, I had Deleted just the one line as suggested in Verbeck's earlier reply to this query, and still there is no Splash Screen. The Option Parameters / Basic / Select default OS to Boot  has nothing in the Drop-Down, and in Parameters / Advanced Parameters I am lost but I do see "quiet splash". Nothing happens when I click Change.[/QUOTE]

Deleting those lines would only clean up your sources list, nothing to do with burg or your splash screen.

I'm sorry I cannot offer any help with burg, I know nothing about it, have never used it or seen it in use. If no one offers any further advice about burg here you could consider posting a new topic with burg in the subject line to attract the attention of burg users, I know there are some who look at this forum and they may not see your question with the title this thread has.

---

### Post by fmlyrnn on 2010-12-31
> **QLee said:**
> Deleting those lines would only clean up your sources list, nothing to do with burg or your splash screen.
 
I'm sorry I cannot offer any help with burg, I know nothing about it, have never used it or seen it in use. If no one offers any further advice about burg here you could consider posting a new topic with burg in the subject line to attract the attention of burg users, I know there are some who look at this forum and they may not see your question with the title this thread has.
 
 
Thank you for your reply! I found out that after the initial update of burg-manager you have to click the button to add to MBR. Issue resolved, and thanks to everyone. 
Note: I will make the cleanup in my Source List.

---

