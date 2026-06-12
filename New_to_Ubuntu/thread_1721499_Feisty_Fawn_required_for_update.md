---
title: "Feisty Fawn required for update"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by gerryl on 2011-04-04
I first started using Ubuntu several years ago with Feisty Fawn.  I have updated as new versions were released, so I now have Maverick 10.10, Linux Kernel 2.6.35-28, Gnome 2.32.0.  Every few days my Update Manager flag comes on, tells me there are updates, but I have to mount the Feisty Fawn disk to upgrade.  When I mount the disk the updates seem to go smoothly.  This does not happen for all updates.  This started a few months ago when I updated to 10.10.  Any suggestions.

---

### Post by Joe of loath on 2011-04-04
Post the output of

```
cat /etc/apt/sources.list
```

---

### Post by rosencrantz on 2011-04-04
Did you run a dist-upgrade recently?
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
(not sure whether second line is necessary, but can't hurt)
Cheers,
rosencrantz

---

### Post by coffeecat on 2011-04-04
Have a look in System > Administration > Synaptic. Now Settings menu > Repositories > Ubuntu Software tab. Is there anything showing in the "Installable from CD-ROM/DVD" field? If there's a tick-box, then untick it.

---

### Post by Joe of loath on 2011-04-04
> **coffeecat said:**
> Have a look in System > Administration > Synaptic. Now Settings menu > Repositories > Ubuntu Software tab. Is there anything showing in the "Installable from CD-ROM/DVD" field? If there's a tick-box, then untick it.


Or do that instead of my suggestion. Much easier :p

---

### Post by gerryl on 2011-04-04
OK - ran the apt-get update command.  Get a lot of output of the form:
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources

Ended with a request to mount the Feisty Fawn disk and press Enter.  Got more output of form:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/ feisty/main Translation-en
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/ feisty/main Translation-en_US

Run remaining two commands.  Got:
gerry@dell:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

gerry@dell:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Not clear on what is happening or if this solved anything.

---

### Post by gerryl on 2011-04-04
> **coffeecat said:**
> Have a look in System > Administration > Synaptic. Now Settings menu > Repositories > Ubuntu Software tab. Is there anything showing in the "Installable from CD-ROM/DVD" field? If there's a tick-box, then untick it.

Installable from CD-ROM/DVD field says:
"To install from a CD-ROM or DVD, install the medium into the drive." 
There is no tick-box in that field.  There are five tick-boxes above this field under the heading "Downloadable from the Internet."  The first four are checked.

The output from the sources.list command is:

```
gerry@dell:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse


deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
```

---

### Post by CharlesA on 2011-04-04
That explains it.

Go to System > Administration > Software Sources

And uncheck anything under cdrom.

---

### Post by gerryl on 2011-04-04
OK - under Other Software the was a box checked for "Cdrom with Ubuntu 7.04 Feisty Fawn."

Unchecked it - hope this solves the problem.  I guess time will tell.

Thank you all for your support.

---

