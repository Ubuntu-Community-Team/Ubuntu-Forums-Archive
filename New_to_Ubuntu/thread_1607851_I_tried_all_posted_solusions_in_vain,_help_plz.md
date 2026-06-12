---
title: "I tried all posted solusions in vain, help plz"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-10-28
My device is hp mini 110-1000 I installed ubuntu netbook 10.10 it worked pretty well and amazing world for me as a first user of linux what thundered it all that I tried to fix the wireless through the synaptic as [COLOR=Red]These package contains Broadcom 802.11 Linux STA wireless driver
for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and
BCM4322-based hardware [/COLOR]
but error error all the time, the message error say:
> E: The method driver /usr/lib/apt/methods/hftp could not be found.
E: Unable to lock the download directory
:mad:
this is first and second:
I rtied all the solusions i the forum to make the software center work but also no way
it says: > There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry
I tried to report the bug mentioned in this error but the site didn't open so also tried many similar solutions on threads around the forum and Oops it is hard I can't start amusing the new linux world
the same errors also in root tries 
what should I do? please now this is my third day and all my work stopped
please help

---

### Post by MooPi on 2010-10-28
Let's try to use the terminal to correct your errors. Open a terminal and type this ```
sudo apt-get update
``` You'll have to enter your password and then it should begin to download updates.
If that comes back with error lets us know.

---

### Post by fatharraxman on 2010-10-28
> **MooPi said:**
> Let's try to use the terminal to correct your errors. Open a terminal and type this ```
sudo apt-get update
``` You'll have to enter your password and then it should begin to download updates.
If that comes back with error lets us know.

Thank you 
you are amazing I didn't  expect such a quick answer 
the root keep says 
[COLOR=Red]E: The method driver /usr/lib/apt/methods/hftp could not be found.
E: The method driver /usr/lib/apt/methods/hftp could not be found.
[COLOR=DarkGreen]_***what should I do plz? :confused:***_[/COLOR][/COLOR]

thank you again

---

### Post by anarchy404 on 2010-10-28
I googld your error output and found a post that might pertain to you: [http://ubuntuforums.org/showthread.php?t=90441](http://ubuntuforums.org/showthread.php?t=90441)

It's possible apt may be broken for you

---

### Post by MooPi on 2010-10-28
I've noticed that your error says " hftp" instead of http and this is odd. Can you post the contents of your ```
/etc/apt/sources.list
```

---

### Post by fatharraxman on 2010-10-28
bash: /etc/apt/sources.list: Permission denied

---

### Post by Grenage on 2010-10-28
> **fatharraxman said:**
> bash: /etc/apt/sources.list: Permission denied

```
cat /etc/apt/sources.list
```

---

### Post by fatharraxman on 2010-10-28
> **Grenage said:**
> ```
cat /etc/apt/sources.list
```
WAW
I typed your code it responded the following  (I understood zero):
> root@ubuntu:/home/fatharrahman# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:/home/fatharrahman# /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
root@ubuntu:/home/fatharrahman# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [ftp://help.ubuntu.com/community/UpgradeNotes](ftp://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb hftp://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [ftp://archive.canonical.com/ubuntu](ftp://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [ftp://extras.ubuntu.com/ubuntu](ftp://extras.ubuntu.com/ubuntu) maverick main
# deb-src [ftp://extras.ubuntu.com/ubuntu](ftp://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security universe
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security multiverse
root@ubuntu:/home/fatharrahman# 
 what next please????:confused:

---

### Post by MooPi on 2010-10-28
I found the error.Try this ```
gksu gedit /etc/apt/sources.list
```
Use Ctrl + f to find hftp
Any instance of hftp change to http. Save and close then reattempt to up date your computer ```
sudo apt-get update 
```

---

### Post by fatharraxman on 2010-10-28
> **MooPi said:**
> I found the error.Try this ```
gksu gedit /etc/apt/sources.list
```Use Ctrl + f to find hftp
Any instance of hftp change to http. Save and close then reattempt to up date your computer ```
sudo apt-get update 
```
it keeps giving the following i mean as if root is  not understanding
> root@ubuntu:/home/fatharrahman# gksu /etc/apt/sources.list
root@ubuntu:/home/fatharrahman# gksu /etc/apt/sources.list
root@ubuntu:/home/fatharrahman# gksu /etc/apt/sources.list
root@ubuntu:/home/fatharrahman# 
 
I feel am close to a solution at end thank you Guys 
what should I do plz:confused:

---

### Post by Daveth on 2010-10-28
you have missed out the text editor "gedit" in his command. What he is telling you is to open it graphically as a super-user, then you can change your wrong value, save, close, and then update.

---

### Post by MooPi on 2010-10-28
Sorry for the error try ```
gksu gedit /etc/apt/sources.list
```

---

### Post by fatharraxman on 2010-10-28
> **MooPi said:**
> Sorry for the error try ```
gksu gedit /etc/apt/sources.list
```
  no problem it opened now am posting it to you in the middle of my changing from ftp to http
hank you again MooPi
then update and tell you 
> # deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
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
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [ftp://archive.canonical.com/ubuntu](ftp://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [ftp://extras.ubuntu.com/ubuntu](ftp://extras.ubuntu.com/ubuntu) maverick main
# deb-src [ftp://extras.ubuntu.com/ubuntu](ftp://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security universe
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by jfreak_ on 2010-10-28
its
gksu gedit /etc/apt/sources.listnot 
gksu /etc/apt/sources.list

you forgot to include 'gedit' . FYI its the name of the text editor

Edit:
Whoops ,too late

---

### Post by jfreak_ on 2010-10-28
> **fatharraxman said:**
> no problem it opened now am posting it to you in the middle of my changing from ftp to http
hank you again MooPi
then update and tell you

Noooo
I think MooPi meant changing hftp to http. Don't change ftp to hftp

---

### Post by fatharraxman on 2010-10-28
[COLOR=Blue]_[FONT=Comic Sans MS][SIZE=3]**Happily after 72 hours of my first ubutu handling with error and horror and time -money wasting**[/SIZE][/FONT]_[/COLOR][SIZE=3][COLOR=Green] it started guys, so fast solutions that's targeted the  kernel of my upsets [/COLOR][/SIZE]
[FONT=Arial][SIZE=5][COLOR=Red]So thank you very very much[/COLOR][/SIZE][/FONT]
it is updating now 
after the finish of update and tries to fix drivers and software centre success I'll tag this thread as solved I hope not to return again with that horrible errors till then
[SIZE=7][COLOR=Red]Thank you again[/COLOR][/SIZE]
:popcorn:
:guitar:

---

### Post by Daveth on 2010-10-28
our collected pleasure :)

---

### Post by Mark Phelps on 2010-10-28
text removed

---

