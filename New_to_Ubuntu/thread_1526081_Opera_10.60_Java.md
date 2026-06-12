---
title: "Opera 10.60 Java"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by rosswmcgee on 2010-07-07
Opera 10.60 Java Applets work in Fedora 13 Mint Isadora but not in Ubuntu 

10.04.

The former use Sun Java 6 jre. I can't install Sun Java Jre in Ubuntu 10.04

it uses Iced Tea. Or at least I think that is the problem. Applets do work

in FireFox.

---

### Post by fooman on 2010-07-07
> **rosswmcgee said:**
>  I can't install Sun Java Jre in Ubuntu 10.04



why not?  have you tried synaptic (system > administration > synaptic package manager)?

search for and install the package "sun-java6-jre"

---

### Post by yeats on 2010-07-07
> The former use Sun Java 6 jre. I can't install Sun Java Jre in Ubuntu 10.04 it uses Iced Tea. Or at least I think that is the problem. 

You *can* install Sun Java JRE. It's a package called sun-java6-jre in the "universe" repository (if I recall).

> Applets do work in FireFox.

If applets work in Firefox, then the installed version of Java isn't the problem.  I'm not sure what to advise, but hopefully this helps.

---

### Post by gandaran on 2010-07-07
on ubuntu 10.04 you have to enable the canonical-partner repository in software sources to get the sun-java packages.
you can then remove all open-java packages and install sun-java.
> it uses Iced Tea. Or at least I think that is the problem. Applets do work

in FireFox.
they work in firefox because firefox uses the java plugin either iceded-tea or sun-java6-plugin while Opera doesn't use the plugin but the path to java which you may have to indicate where Opera can find java if it doesn't pick it up.

---

### Post by rosswmcgee on 2010-07-07
I did that before I wrote this, but it did not accept sun java, so do you mean I must remove the iced tea before installing the sun java?
  

Removed Iced Tea//tried installing sun6jre// got this

sun-java6-jre:

Package sun-java6-jre has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

This is what I get in synaptix. 

Was this change to iced tea necessary?

---

### Post by rosswmcgee on 2010-07-07
sun-java6-jre:

Package sun-java6-jre has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

This is what I get in synaptix.

---

### Post by gandaran on 2010-07-08
> **rosswmcgee said:**
> sun-java6-jre:

Package sun-java6-jre has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

This is what I get in synaptix.
did you enable the canonical-partner repository in software sources and reloaded synaptic data? ( or sudo apt-get update)

---

### Post by rosswmcgee on 2010-07-08
I checked every box in the software sources other and other variations// this is what I get///

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead. or 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file

It would be helpful to know what is to be checked in Software sources Ubuntu software and other..

---

### Post by fooman on 2010-07-08
open synaptic package manager.  in the toolbar,  click: settings > repositories
in the "software sources" box that opens up,  look under the "ubuntu software" tab and make sure the first 4 choices are all checked (main - universe - restricted - multiverse)
click the closed button.

back in synaptic,  click the "reload" button to add/refresh the newly added repos.  then search for sun-java6-jre again.

hope that helps.

---

### Post by QIII on 2010-07-08
As stated above, Java 6 Update 20 (the most recent version) is in the *Partner* repository.

---

### Post by Metrop021 on 2010-07-08
go to opera:plugins

and make sure that you see /usr/lib/mozilla/plugins/libflashplayer.so (or something similar)

java is working well for me on opera 10.60

---

### Post by rosswmcgee on 2010-07-08
are you using ubuntu 10.04??

---

### Post by rosswmcgee on 2010-07-08
Thanks for you help but when I reload I get this///

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by rosswmcgee on 2010-07-08
Yes it has that.. also are you using icedtea or sun java?

---

### Post by QIII on 2010-07-09
> **rosswmcgee said:**
> Thanks for you help but when I reload I get this///

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Try a different server.  That one may be having problems.

System | Administration | Software Sources

Change the selection in the drop down to "Main Server" and try again.

There is some contention about this, so take it for what it is worth:

There are some who say that having IcedTea and Sun Java on the machine at the same time causes conflicts.  I am not convinced one way or the other.  Personally, I uninstalled IcedTea.

Try that and let us know what happens.

---

### Post by rosswmcgee on 2010-07-09
I have swithched to the main server from the United States server, but still get failed to fetch msg. I have the first four checked under ubuntu software under other soft ware I have [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) checked. That is it. Also I seem to be unable to log in terminal//I type su it asks for password I tyoe in the password and get authentification failure// but I am already at rosswmcgee@rosswmcgee-desktop:~$

so maybe the su command is not needed?/

---

### Post by QIII on 2010-07-09
Use sudo to elevate your privileges, not su.

---

### Post by rosswmcgee on 2010-07-09
This what I get from sudo////

rosswmcgee@rosswmcgee-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by QIII on 2010-07-09
```
sudo <some command>
```

or, for something that is done in a GUI:

```
gksudo <some command>
```

is how you go about getting something done with sudo.

The rather cryptic stuff you are getting is pretty much the same as

"OK.  So, sudo.  sudo what?  What do you want me to do?"

---

### Post by fooman on 2010-07-09
could you post the contents of your /etc/apt/sources.list file?  ...open a terminal and type or copy/paste the following command:

```
gedit /etc/apt/sources.list
```when it opens, copy and paste the entire contents back here.

---

### Post by rosswmcgee on 2010-07-09
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main'. main universe restricted multiverse

---

### Post by fooman on 2010-07-10
is that the entire contents of the file?
 
are you running karmic (9.10) or lucid (10.04)?

---

### Post by rosswmcgee on 2010-07-10
Yes that is it I am runing 10.04. It is an upgrade from karmic

---

### Post by fooman on 2010-07-10
try editing that file (system file so you need to be root) and *comment out* that karmic line (type a # at beginning of line to make it invisible)... open a terminal and type or copy/paste:

```
gksudo gedit /etc/apt/sources.list
```when it opens, scroll down to that last section,  and place a # in front of the line:

```
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
```so that the section looks like this afterwards:
```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
```then save, and close the file.  next, while the terminal is still open....update the repos and install sun-java6-jre by running the following commands, one at a time:

```
sudo apt-get update
sudo apt-get install sun-java6-jre
```or you could go back to synaptic, refresh the repositories by pressing the "reload" button,  then search for and install "sun-java6-jre". 

hope that helps.

---

### Post by rosswmcgee on 2010-07-11
I don't mind doing the above recommedation, however I just realized that in Ubuntu 10.04 synaptic there is no option for a Sun Java6 plugin. With out the plugin the jre and bin sun java won't work anyway.  So does the ubuntu clean install 10.04 have all the Sun Java or not? If not I can install Mint which has it all and everything works in about an hour and be done. I want to keepm at least one computer on Ubuntu though just to see whats happening.

---

### Post by gandaran on 2010-07-11
> **rosswmcgee said:**
> I don't mind doing the above recommedation, however I just realized that in Ubuntu 10.04 synaptic there is no option for a Sun Java6 plugin. With out the plugin the jre and bin sun java won't work anyway.  So does the ubuntu clean install 10.04 have all the Sun Java or not? If not I can install Mint which has it all and everything works in about an hour and be done. I want to keepm at least one computer on Ubuntu though just to see whats happening.
if you are running 64-bits ubuntu, no, forget it there is no sun-java6 plugin in synaptic, but you can still go to the sun-java website and download 64-bits sun-java, it will be a bit hard for you to install,  you can find the linux instructions at the sun website too.
if it's 32-bits ubuntu you have then yes, you can find the plugin in synaptic after enabling the partner repository.
you sources list is a mess, if you are really running 10.04 I suggest you remove all the karmic entries from the sources list then go to software sources and enable/disable all the recommended repositories just to see if it will create the correct 10.04 entries.
or just wait for someone here to provide the full local US sources.list then just copy them to your system.

---

### Post by fooman on 2010-07-11
> **gandaran said:**
> 
or just wait for someone here to provide the full local US sources.list then just copy them to your system.

if you need it....heres the sources.list on my 64bit, lucid install:


```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
```

---

### Post by QIII on 2010-07-12
I really hope that there is still someone reading this.

The 64 bit Sun Java 6 plugin IS, in fact, available in the repos.  

In Lucid, it IS NOT necessary to install from Sun's website.  Sun has made its packages available for Canonical to put in the Partner repo.

All that is needed is for the user to activate the Partner repository.

Here, from my machine after installing from the Partner repo, as show in about: plugins

/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libnpjp2.so

libnpjp2.so is the official Sun 64 bit plugin.

---

### Post by gandaran on 2010-07-12
> **QIII said:**
> I really hope that there is still someone reading this.

The 64 bit Sun Java 6 plugin IS, in fact, available in the repos.  

In Lucid, it IS NOT necessary to install from Sun's website.  Sun has made its packages available for Canonical to put in the Partner repo.

All that is needed is for the user to activate the Partner repository.

Here, from my machine after installing from the Partner repo, as show in about: plugins

/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libnpjp2.so

libnpjp2.so is the official Sun 64 bit plugin.
okay, sorry then, I didn't know this long time 64-bits java plugin problem is finally fixed.

---

### Post by QIII on 2010-07-12
The issue was fixed near the end of May, I believe.  It was not that the 64 bit plugin did not exist, simply that it did not end up in the Mozilla plugins directory.

In that case, all that was needed was the following:

```
sudo update-alternatives --install
/usr/lib/mozilla/plugins/mozilla-javaplugin.so  mozilla-javaplugin.so
/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so  1
```

---

### Post by rosswmcgee on 2010-07-12
osswmcgee@rosswmcgee-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main'. Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
rosswmcgee@rosswmcgee-desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

---

### Post by gandaran on 2010-07-12
> **rosswmcgee said:**
> osswmcgee@rosswmcgee-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main'. Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
rosswmcgee@rosswmcgee-desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
forget it man, you sources list is not complete, theres no archive-canonical repo there, so maybe it's just better to reinstall Ubuntu or get hold of the full correct 32-bits or 64-bits (I not sure what you have but maybe it's 32-bits) sources list.

---

### Post by rosswmcgee on 2010-07-12
Last question.

will the new release coming in the fall fix it or should I do a clean install?

---

### Post by fooman on 2010-07-12
from the look of your sources.list file....i would go for the fresh install.

i had posted my sources.list file in an earlier post (see post # 27),  you could first make a copy of your present sources.list file.  then delete the original's contents and replace it with mine.  then try to update....see if that works.

if it does not work....just copy the old file back.

might be worth a shot before you go and reinstall.

to copy the file (and rename the new file) run this command:

```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```that will make a copy of your present file and name it "sources.list.old".

next open the file for editing as root, with this command:

```
gksudo gedit /etc/apt/sources.list
```delete everything in there and replace with the contents of my file which i posted earlier.

save and close the file... try synaptic again.  refresh the repos first,  then search for sun java and if it finds them: install.

hope that helps.

---

### Post by rosswmcgee on 2010-07-12
Thanks everyone. Enough on this question a new install is the way to go.

---

### Post by fooman on 2010-07-12
> **rosswmcgee said:**
> Thanks everyone. Enough on this question a new install is the way to go.

you could try what i posted above before reinstalling.....would only take you a minute or 2.

might save you a lot of trouble.

---

### Post by rosswmcgee on 2010-07-12
Yes I did, but to no avail. This Ubuntu computer  had been upgraded several times, so I am doing a clean install at this time. I will go directly to synaptic and see whats what on the new install. Ok how do get the sun java in ubuntu clean install does not have the plug in or sun java 6jre. So opera applets do not work and I am dissatisfied, I see no reason for not moving to Mint.  To my mind Opera is the best browser available, for instance all my other distros opera can read applets except ubuntu 10.04.



 Thanks again.

---

### Post by gandaran on 2010-07-13
> **rosswmcgee said:**
> Yes I did, but to no avail. This Ubuntu computer  had been upgraded several times, so I am doing a clean install at this time. I will go directly to synaptic and see whats what on the new install. Ok how do get the sun java in ubuntu clean install does not have the plug in or sun java 6jre. So opera applets do not work and I am dissatisfied, I see no reason for not moving to Mint.  To my mind Opera is the best browser available, for instance all my other distros opera can read applets except ubuntu 10.04.



 Thanks again.
you did the right thing reinstalling, enable the archive-canonical partner repository in software sources then run the update and install commands
```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```
the plugim install command is enough to install all java packages, the jre and bin package are automatically installed too. 
install the java before installing Opera so it can pick it up, if it doesn't pick up java I will show you how to do it.
and be careful about installing the ubuntu-restricted-extras package, this meta package installs openjdk java and ubuntu is configured to use open-java if you have both installed, I would suggest to look at the properties of ubuntu-restricted-extras in synaptic and install all other packages that make up ubuntu-restricted-extas meta package one by one just leave the openjdk out.

---

### Post by rosswmcgee on 2010-07-13
OK got it and Opera Java now works, hip hip hooray! I can see the problem now in software sources in the upgrade version the choices were different than they are 
in the clean install. So in trying to follow previous helpful advise I was always on a
different page so to speak. Thanks again every one from now on it is going to be clean installs, I just got lazy.
This time I made a note of every thing I need to do upon a clean install. Here is what I came up with.

enable the archive-canonical partner repository in software sources then run the update and install commands

sudo apt-get update
sudo apt-get install sun-java6-plugin

GUI Printer

Trash Bin on Desktop Alt F2 //gconf-editor//apps\nautilus\desktop\trashcan visible.

Flash Player Plug In+Flash Player non freeenable the archive-canonical partner repository in software sources then run the update and install commands

sudo apt-get update
sudo apt-get install sun-java6-plugin

GUI Printer

Trash Bin on Desktop Alt F2 //gconf-editor//apps\nautilus\desktop\trashcan visible.

Flash Player Plug In+Flash Player non free

Have I missed anything?? Of course I save all my address and bookmark stuff.

---

