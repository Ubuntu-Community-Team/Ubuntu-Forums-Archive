---
title: "apt-get problems"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Rosscopico on 2011-06-12
Hi everyone,
I've installed the java rte, & am now trying to get the upgrade with the following command line:-
 sudo apt-get update
 but I keep getting the following message:-
 E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
 E: The list of sources could not be read.
 
 What does that mean & how do I fix it?

Also I've noticed that I get this message with any program update that Ive attempted to do.

---

### Post by sikander3786 on 2011-06-12
Means there is problem in line 62 in your sources.list. Please post the output of this command to let us take a look at that.

```
cat /etc/apt/sources.list
```

---

### Post by kellemes on 2011-06-12
Post **/etc/apt/sources.list**
so we can find the problem..

---

### Post by Rosscopico on 2011-06-12
The output of :- cat /etc/apt/sources.list
was:-
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid

---

### Post by Rosscopico on 2011-06-12
I think I recall using the command line :- deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
while attempting to install Vuze, following some instructions I found on the web.

I have since successfully installed Vuze, but anything I try to update is giving me the Malformed line 62 error

---

### Post by sikander3786 on 2011-06-12
Are you sure that is the complete output you just posted? Try editing it in Gedit and make sure there are no empty lines or invalid characters towards the bottom.

```
gedit /etc/apt/sources.list
```

---

### Post by wolfen69 on 2011-06-12
Are you sure you included everything in **cat /etc/apt/sources.list** ?????

You're not showing 62 lines.

---

### Post by Rosscopico on 2011-06-12
oops - here we go

# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid

---

### Post by sikander3786 on 2011-06-12
Yeah that was a dist parse error regarding the last line that belongs to 'Lucid' and not Natty that you are currently using.

Edit your sources.list:

```
gksudo gedit /etc/apt/sources.list
```

And comment out the last line of that file so it looks like this:

```
[COLOR="Red"]#[/COLOR]deb-src http://archive.canonical.com/ubuntu lucid
```

Save and close this file. Now run:

```
sudo apt-get update
```

---

### Post by Rosscopico on 2011-06-12
Fantastic! Thank you!
However I'm getting the errors:-

```
W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
I assume as its saying "404 not found" its a problem of a website no longer existing?

---

### Post by sikander3786 on 2011-06-12
Yeah those PPAs seem down at the moment.

You can go to Software Center > Edit > Software Sources > Other Software Tab and disable those 2 PPAs.

---

### Post by Rosscopico on 2011-06-12
Thank you all for your help! :D

---

