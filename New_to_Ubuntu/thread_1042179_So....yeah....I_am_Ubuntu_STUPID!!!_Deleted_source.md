---
title: "So....yeah....I am Ubuntu STUPID!!! Deleted sources.list"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by jecarr33 on 2009-01-17
Hey guys, I think I may have messed up.  I just made the switch to Ubuntu from Windows and plan on NEVER going back...however, I think I may have accidentally deleted "sources.list"  how can I get this back??  I am using Intrepid and think that may be an important file.  PLEASE HELP!!  Thanks in advance!!

Jonathan:confused:

---

### Post by taurus on 2009-01-17
Maybe there is a backup copy on your machine.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la /etc/apt
```
Without /etc/apt/sources.list, you won't be able to install anything or update your machine.

---

### Post by earthpigg on 2009-01-17
if you can't find the backup:

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

Source List Generator for Ubuntu

:)

---

### Post by 73ckn797 on 2009-01-17
> **jecarr33 said:**
> Hey guys, I think I may have messed up.  I just made the switch to Ubuntu from Windows and plan on NEVER going back...however, I think I may have accidentally deleted "sources.list"  how can I get this back??  I am using Intrepid and think that may be an important file.  PLEASE HELP!!  Thanks in advance!!

Jonathan:confused:

Did it get put in the trash bin? If so, maybe you could just restore it.

---

### Post by ibizatunes on 2009-01-17
What version of ubuntu do you have? 
```
sudo gedit /etc/apt/sources.list
```
Paste a new source list there once we know what your version is!

---

### Post by nothingspecial on 2009-01-17
Here`s mine, save it as souces.list in /etc/apt
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://apt.wicd.net hardy extras
```

Then sudo apt-get update and you should be good to go. The only thing I`ve added is wicd at the bottom. Leave it out if you like.

---

### Post by albinootje on 2009-01-17
> **jecarr33 said:**
> I am using Intrepid and think that may be an important file.
It's indeed a very important for installing and updating software.
I'll attach mine (From Hardy, but I've edited for usage on Intrepid).
Make sure you copy it to /etc/apt/sources.list !
The .txt is only added to enable the upload as attachment here.

---

### Post by jecarr33 on 2009-01-17
> **taurus said:**
> Maybe there is a backup copy on your machine.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la /etc/apt
```
Without /etc/apt/sources.list, you won't be able to install anything or update your machine.

 ls -la /etc/apt
total 56
drwxr-xr-x   4 root root  4096 2009-01-17 07:50 .
drwxr-xr-x 127 root root 12288 2009-01-16 16:51 ..
drwxr-xr-x   2 root root  4096 2009-01-16 10:48 apt.conf.d
-rw-------   1 root root     0 2008-10-29 16:54 secring.gpg
-rw-r--r--   1 root root  3017 2009-01-16 10:48 sources.list~
drwxr-xr-x   2 root root  4096 2009-01-17 07:49 sources.list.d
-rw-------   1 root root  1200 2009-01-17 07:50 trustdb.gpg
-rw-r--r--   1 root root  9450 2009-01-17 07:50 trusted.gpg
-rw-r--r--   1 root root  9450 2009-01-17 07:50 trusted.gpg~
jonathan@jonathan-desktop:~$

---

### Post by jflaker on 2009-01-17
> **jecarr33 said:**
> Hey guys, I think I may have messed up.  I just made the switch to Ubuntu from Windows and plan on NEVER going back...however, I think I may have accidentally deleted "sources.list"  how can I get this back??  I am using Intrepid and think that may be an important file.  PLEASE HELP!!  Thanks in advance!!

Jonathan:confused:

The dangers of being root?  Copy mine if you can't find a backup.  

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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

```

---

### Post by taurus on 2009-01-17
> **jecarr33 said:**
> ls -la /etc/apt
total 56
drwxr-xr-x   4 root root  4096 2009-01-17 07:50 .
drwxr-xr-x 127 root root 12288 2009-01-16 16:51 ..
drwxr-xr-x   2 root root  4096 2009-01-16 10:48 apt.conf.d
-rw-------   1 root root     0 2008-10-29 16:54 secring.gpg
**[COLOR="Blue"]-rw-r--r--   1 root root  3017 2009-01-16 10:48 sources.list~[/COLOR]**
drwxr-xr-x   2 root root  4096 2009-01-17 07:49 sources.list.d
-rw-------   1 root root  1200 2009-01-17 07:50 trustdb.gpg
-rw-r--r--   1 root root  9450 2009-01-17 07:50 trusted.gpg
-rw-r--r--   1 root root  9450 2009-01-17 07:50 trusted.gpg~
jonathan@jonathan-desktop:~$

There's your backup copy.  

```
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
```
Now, have a look to make sure everything in there is right.

```
cat /etc/apt/sources.list
```

---

### Post by jecarr33 on 2009-01-17
> **jflaker said:**
> The dangers of being root?  Copy mine if you can't find a backup.  

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

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

```


Ok, WOW!! so many replies very very very helpful...and so fast.  I have the new sources.list file saved and now I need to move it to /etc/apt but I keep getting denied access.  I'm sure I have to change the permissions but rather than doing something crazy is there just a better way to get it to allow the transfer once?  Or do I have chown the folder or chmod it?

Another thing, How do I switch it so I'm NOT root and can't do that again?? I need t learn this lingo :confused:

Thank you so much in advance for the help.  I'm loving Linux, but apparently I need a class!!! LOL!!

-Jonathan

---

### Post by damis648 on 2009-01-17
All you need to do at this point is follow taurus' advice:
```
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
sudo apt-get update
```

---

### Post by earthpigg on 2009-01-17
> **jecarr33 said:**
> Another thing, How do I switch it so I'm NOT root and can't do that again?? I need t learn this lingo :confused:

Thank you so much in advance for the help.  I'm loving Linux, but apparently I need a class!!! LOL!!

-Jonathan

speaking from my own experience, these forums are all the edumication you need.

any time you type 'sudo' **or** run a program that asks you to put your password in, you are root.

if you type 'sudo' or 'gksudo' or anything like that, it makes you root for the next 15 minutes and a typo can then jack your entire system up... so be careful ;)

sudo is '_S_uper _U_ser _DO_'

edit: super user = root = administrator = god-of-the-system = super user = can break anything with a typo = rawr = root.... clear enough? :)

---

### Post by albinootje on 2009-01-17
> **damis648 said:**
> All you need to do at this point is follow taurus' advice:
```
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
sudo apt-get update
```

Probably correct, and it might work, but.. we don't know what is in that backup file (/etc/apt/sources.list~), therefore this is a tricky suggestion, and possibly wasting time if that backup file is a messed up version.

So.. it's better to copy one of the copies that people already offered, or use the mentioned sources.list generator.

---

### Post by jecarr33 on 2009-01-17
This is SOLVED!!!!  Thank you everyone who helped me to understand just a little bit more about the OS.  I get kind of mad when the OS tells me I don't have permission to do something like move a file and stuff.  I realize this is so I don't do something ridiculous like delete the sources.list file and what not.  So Im assuming that anything with a ~ next to it is a backup.  I wonder how you learn about all these different commands.  Hmmm... thank you all, trying to change the topic to reflect SOLVED

-Jonathan

---

### Post by earthpigg on 2009-01-17
> **jecarr33 said:**
> I wonder how you learn about all these different commands.  

making threads, reading threads on this forum, google, wikipedia, and man pages.

(type 'man ls' for an example of a 'man page'. 'man' = manual.... man *whatever* shows the manual for *whatever* command, is always safe to type, and will not hurt/break anything no matter what or your money back.)

edit: i want to emphasize google again. my goal with google is always: "i want to find someone else that has/had the exact same problem i do, and see how they fixed it."

edit 2: check out the google results for "ubuntu deleted sources.list": [http://www.google.fi/search?hl=en&q=deleted+sources.list+ubuntu&btnG=Search](http://www.google.fi/search?hl=en&q=deleted+sources.list+ubuntu&btnG=Search)

---

### Post by jecarr33 on 2009-01-17
> **earthpigg said:**
> making threads, reading threads on this forum, google, wikipedia, and man pages.

(type 'man ls' for an example of a 'man page'. 'man' = manual.... man *whatever* shows the manual for *whatever* command, is always safe to type, and will not hurt/break anything no matter what or your money back.)

edit: i want to emphasize google again. my goal with google is always: "i want to find someone else that has/had the exact same problem i do, and see how they fixed it."

edit 2: check out the google results for "ubuntu deleted sources.list": [http://www.google.fi/search?hl=en&q=deleted+sources.list+ubuntu&btnG=Search](http://www.google.fi/search?hl=en&q=deleted+sources.list+ubuntu&btnG=Search)

The whole "man" command is GANGSTER!!!   it's GANGSTER!!!  Thanks for that one.!!!

---

### Post by albinootje on 2009-01-17
> **earthpigg said:**
> making threads, reading threads on this forum, google, wikipedia, and man pages.

(type 'man ls' for an example of a 'man page'. 'man' = manual.... man *whatever* shows the manual for *whatever* command, is always safe to type, and will not hurt/break anything no matter what or your money back.)

This is a good start :
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://linuxcommand.org/](http://linuxcommand.org/)

Personally, and depending on the question, I tend to search for howtos rather than using man pages, because *some* man pages have an overwhelming overload of information, and most of that information you won't need normally.

Years ago man pages in Linux were much worse, now several man pages have examples. 
The examples in the man pages are very nice to have.
Usually the examples are at the end of the man page.

---

