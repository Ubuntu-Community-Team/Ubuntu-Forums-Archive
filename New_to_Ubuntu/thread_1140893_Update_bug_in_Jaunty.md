---
title: "Update bug in Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by the8thstar on 2009-04-28
Hello guys,

Whenever I perform an update in Jaunty, I get the same message: 

> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CE90D8983E731F79


How can I get the right key? Thanks for your help!

---

### Post by halovivek on 2009-04-28
HI
please check this [link]("http://izanbardprince.wordpress.com/2009/03/26/how-to-fix-ubuntu-jaunty-warning-hacks-ahead/"). it will help you more for solution.

---

### Post by Anthon on 2009-04-28
Looks like you have an entry in /etc/apt/sources.list or file in /etc/apt/source.list.d
that use something not from the 'normal' repository (ppa -> personal package archive)
Look up that application and it probably has (not very userfriendly) instructions on how to install the proper key.
E.g. I use a ppa for pidgin:
  [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
and I followed the line on that page:
This repository is signed with  1024R/A1F196A8 OpenPGP key. Follow these instructions  for installing packages from this PPA.

---

### Post by kansasnoob on 2009-04-28
We'll need to see the output from terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by PatrikG on 2009-04-28
I had a similar problem. I did something like this:

Go to: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79)

(this is edited with your key)

make a text file with the text output that you get from the homepage.

go to the Synaptic manager and import the key file in the settings menu.

Hope it works!

---

### Post by the8thstar on 2009-04-28
Okay, here goes:

> # deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe #Added by software-properties
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free #skype
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main #compiz-fusion
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #medibuntu
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main #avant-window-navigator
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main #gnome-globalmenu
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

---

### Post by the8thstar on 2009-04-28
> **PatrikG said:**
> I had a similar problem. I did something like this:

Go to: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79)

(this is edited with your key)

make a text file with the text output that you get from the homepage.

go to the Synaptic manager and import the key file in the settings menu.

Hope it works!

Good idea. Unfortunately, Synaptic doesn't 'see' the text file.

---

### Post by Pisi-Deff on 2009-04-28
Try this:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com *number*
```
In your case it'd be:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CE90D8983E731F79
```

Worked for me :)

---

### Post by the8thstar on 2009-04-28
It did the trick! Thank you very much for your help everybody.

---

