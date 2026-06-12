---
title: "No internet connection"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Noobinvader1 on 2009-01-21
Hi I am very new to Linux and am having problems installing an application called Kstars. Every time it try in the add/remove applications it wants to update the list of available applications. when I click reload it starts to download it looks like then comes up with an error that says:

"Could not download all repository indexes:

     The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. check your network connection and correct writing of the repository address in the preferences."

after that in a box it gives the Http: address of several Ubuntu community sites.

My question is with an always on cable connection could it be my connection if so how do I fix that, If not what do I need to do to download the applications I want to use?

Thanks for any help.

---

### Post by DougieFresh4U on 2009-01-21
I don't if this would help, but are your repo's checked in Software Sources? Also have you tried to install from terminal?
Just a thought.

---

### Post by Bölvaður on 2009-01-21
It could be that the repo server you are connecting to doesnt have all the packages, or that you do not have universe and multiverse repos allowed. You say you are on ubuntu so it should be System &#8594; Administration &#8594; System Sources and tick all except source code (well it isnt worse to have it), then go System &#8594; Administration &#8594; Synaptic Package manager, lookup kstars and try install it again.

if that fails open up the terminal (Applications &#8594; Accessories&#8594;Terminal) and copy and paste (ctrl+shift+v)
```

sudo apt-get install kstars
```

and send us the error code again

*added*
also if it fails send us the output from this command... or let us see the content of the sources.list file how ever you choose to do so. 
```
cat /etc/apt/sources.list
```

---

### Post by Noobinvader1 on 2009-01-21
I checked to see if the sources were all checked and they are. 

This is a copy of the source codes that I got from the term window

jeremy@jeremy-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
jeremy@jeremy-laptop:~$ 


not sure what to do from there.

---

### Post by Miljet on 2009-01-21
What version of Ubuntu are you using. Fiesty Fawn is no longer supported. Looks like you are overdue for an upgrade.

---

### Post by Noobinvader1 on 2009-01-21
Ubuntu 7.04 is what i have at this point.

---

### Post by Noobinvader1 on 2009-01-23
Downloaded Ubuntu 8.10 It works great thanks for the help

---

