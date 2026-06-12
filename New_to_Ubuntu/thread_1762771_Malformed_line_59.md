---
title: "Malformed line 59"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by RDC13 on 2011-05-19
Help, please.  I guess I messed up something somehow.  Everytime I try to update or add software, I can't.  Instead I get an error messages:  ```
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```
I've looked at other forums and generally those who are offering help say they need the software sources list.  Here it is:
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
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
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) main ## Cairo-Dock-PPA-Stable
```

---

### Post by compmodder26 on 2011-05-19
Remove "## Cairo-Dock-PPA-Stable" at the end.  That should fix you up.

---

### Post by wolfen69 on 2011-05-19
> **compmodder26 said:**
> Remove "## Cairo-Dock-PPA-Stable" at the end.  That should fix you up.

Just remember to do
```
sudo apt-get update
```
after.

---

### Post by RDC13 on 2011-05-21
Thanks.  As I said, I'm am really at the absolute basic level.  I ran the "gedit /etc/apt/sources.list" command, but I can't delete the line. How do I remove it?

---

### Post by RDC13 on 2011-05-21
One more question, just so I learn how to do this myself, what are you looking for that allows you to determine which line should be deleted?  BTW, I really appreciate the help on this. Thanks.

---

### Post by howefield on 2011-05-21
> **RDC13 said:**
> I ran the "gedit /etc/apt/sources.list" command, but I can't delete the line.

Use the command

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by steveneddy on 2011-05-21
If you are currently using cairo dock then simply open the file and comment out the line with a 

```
#
```

then 

```
sudo apt-get update
```

This will tell the computer not to look at that line until you figure out what is wrong with it.

Also when you do that you cairo dock will not get updated, so go figure out what is wrong with the ppa line and change it to correct the issue.

---

### Post by compmodder26 on 2011-05-21
He knows what the problem is, he just needs to get rid of that trailing "## Cairo-Dock-PPA-Stable" at the end of the file.  howefield's advice should get him fixed up on the issue of not being able to save the changes he's made.

---

### Post by Plueonic on 2011-05-21
> **compmodder26 said:**
> He knows what the problem is, he just needs to get rid of that trailing "## Cairo-Dock-PPA-Stable" at the end of the file.  howefield's advice should get him fixed up on the issue of not being able to save the changes he's made.
A simple comment at the end of the line wouldn't cause any issues. He is missing the distributions name there, i.e;
```
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu main
```should be
```
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu maverick  main
```

---

### Post by compmodder26 on 2011-05-21
> **Plueonic said:**
> A simple comment at the end of the line wouldn't cause any issues. He is missing the distributions name there, i.e;
```
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu main
```should be
```
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu maverick  main
```

:oops: Hehe, completely missed that.  You are correct.  Apologies go to steveneddy.

---

