---
title: "HELP! Major Failure of Software Management"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by leenyx64 on 2009-01-19
Okay so I just got this cool little netbook last week and install Ubuntu 8.10 on it two days ago (so far so good). However, today I was trying to update the multimedia feature by (attempting) to follow [this thred.]("http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia")

Okay so I then was trying to access the Add/Remove under Applications and I got a "Major Failure of Software Management Systems"

Here is a paste from my source list:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main


PLEASE Help

---

### Post by hyper_ch on 2009-01-19
run in the terminal:
```

sudo apt-get update && sudo apt-get upgrade

```
and post the output here.

---

### Post by blackened on 2009-01-19
To pin down the exact problem, run these two commands:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

If your sources.list file has problems, then the first command should tell you the line-number that the problem is on.

**Edit:** man I'm slow tonight.

---

### Post by bailbath on 2009-01-19
Hopefully there is nothing of importance on your netbook.
Please backup anything important
Just re-install for a quick fix
Then try again. It is easy to make a small mistake we all have done that.
Ian

---

### Post by blackened on 2009-01-19
> **bailbath said:**
> Hopefully there is nothing of importance on your netbook.
Please backup anything important
Just re-install for a quick fix
Then try again. It is easy to make a small mistake we all have done that.
Ian

Yeah, I don't think that will be necessary. Stuff like this can happen over something as stupid as a typo in sources.list, though I don't see anything just by scanning over it quickly. If it's a bug, it's better to find and report it than to ignore it and expect it to go away on its own.

---

### Post by leenyx64 on 2009-01-19
when I run:

sudo apt-get update && sudo apt-get upgrade

it yields 

E: Type '<!DOCTYPE' is not known line 3 in source list /etc/apt/sources.list.d/mediabunt.list

Sorry for responding so late.  I have midterms this week and fell asleep early last night.  I do really appreciate the help everyone.

---

### Post by perce on 2009-01-19
> **leenyx64 said:**
> when I run:

sudo apt-get update && sudo apt-get upgrade

it yields 

E: Type '<!DOCTYPE' is not known line 3 in source list /etc/apt/sources.list.d/mediabunt.list



It looks like there is an unknown character in the file 

```
/etc/apt/sources.list.d/mediabunt.list 
```

you created this file, probably, by following the instruction

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

from the thread you have indicated. My guess is that you can remove that file (be careful not to remove the main source.list) and install multimedia stuff by

```
 sudo apt-get install ubuntu-restricted-extras 
```
it has all what you need, except DVD playback, which can be enabled following the instructions in he wiki:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by hyper_ch on 2009-01-19
medibuntu wasn't correctly downloaded... delete the /etc/apt/sources.list.d/mediabunt.list file and you should be ok again.

---

### Post by leenyx64 on 2009-01-19
Thanks a lot hyper_ch and perce. One more question and I think I may have this fixed.  I am trying to delete the *mediabuntu.list* file but it says that I dont own the file and cannot change the permissions. Also there is a *mediabuntu.list.save* file in the same directory, should I also delete that.

---

### Post by jimmy the saint on 2009-01-19
you can either open up a nautilus session with root privilages, or do it through the command line.
to open nautilus with roo privilages open a terminal and type
```
gksudo nautilus
```
BE CAREFUL.  you can frag your system if you arent careful.  you have a lot of power!

Alternately, you can preface the rm command with sudo to remove the file.

```
sudo rm <file>
```
where <file> is the file you want to remove. that will grant you temporary root privilages.

---

### Post by leenyx64 on 2009-01-19
All fixed :P You guys are the best. Thanks

---

