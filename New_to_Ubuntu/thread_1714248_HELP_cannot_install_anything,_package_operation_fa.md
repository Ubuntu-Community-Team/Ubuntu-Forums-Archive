---
title: "HELP cannot install anything, package operation failed"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by grapitypurple on 2011-03-25
I've been using ubuntu for a couple of months now, version 10.10. for the past week or so whenever I try to install upadates or software or anythign at all I get a package operation failed error. I have googled the crap out of the error messages and tried the recommendations, but so far absolutely nothing has worked. this is the error I get when trying to update:

nstallArchives() failed:  Extracting templates from packages: 85% Extracting templates from packages: 100% 
Preconfiguring packages ... 
 Extracting templates from packages: 85% Extracting templates from packages: 100% 
Preconfiguring packages ... 
dpkg: unrecoverable fatal error, aborting: 
 syntax error: invalid uid in statoverride file 


I get similar errors whenever I try to install anything, this didn't happen until recently. any help?

---

### Post by jtarin on 2011-03-25
First, if you can outline your procedure that you are using to attempt this? A walk-thru, fi you will.

[You might try this.]("http://ubuntuforums.org/showthread.php?t=1654201")

---

### Post by grapitypurple on 2011-03-25
> **jtarin said:**
> First, if you can outline your procedure that you are using to attempt this? A walk-thru, fi you will.

[You might try this.]("http://ubuntuforums.org/showthread.php?t=1654201")


I did that already, still get same errors.

---

### Post by jtarin on 2011-03-25
> **grapitypurple said:**
> I did that already, still get same errors.
[Then this]("http://old.nabble.com/Stuff-appearing-in-Terminal,-I-dont-know-what-it-is......-td31079926.html")

---

### Post by grapitypurple on 2011-03-26
Nothing works. My room mate had a look at it for a few hours last night, it turns out that apt is busted and I'm most likely going to have to just reload my computer and start from scratch. It's a shame because up until now I liked using ubuntu.

---

### Post by goldaryn on 2011-03-26
if you type 

```
$ sudo gedit /etc/apt/sources.list
```

into a console, what have you got in that file?

Mine looks like this

```

#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```
which as far as I know is the default. (I think I clicked "allow third party" when I was installing). What has yours got it in?

---

### Post by jtarin on 2011-03-26
Did you add a new user and then deleted it?

---

