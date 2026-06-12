---
title: "problem with update manager"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by captaincornwall on 2011-01-04
For some reason update manager as stopped updating for the last couple of weeks. (I use Ubuntu 10.10 and am loving it after switching form windows. wish I shopped using windows years ago but it took a major virus attack to make the move)

When I try and update I get the following message:

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7, W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C, W:Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/intrepid/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/intrepid/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I am completely new to Linux and have read similar forum post around the net but don't really understand whats happening or how to fix it.

I have tried to reinstall it but with no luck.

would really appreciate some help.

---

### Post by Verbeck on 2011-01-04
if you're using 10.10, those sources should not be there
open a terminal (applications>accessories) and post the output of
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by captaincornwall on 2011-01-04
this is the results

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick main multiverse universe restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates main multiverse universe restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security main multiverse universe restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) intrepid main
prest@prest-OptiPlex-GX270:~$ ls /etc/apt/sources.list.d/

no idea what that means though. It used to work. Can't see why it suddenly stopped?

---

### Post by matt_symes on 2011-01-04
Hi

```
deb http://wine.budgetdedicated.com/apt intrepid main
deb-src http://wine.budgetdedicated.com/apt intrepid main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu intrepid main
deb http://ppa.launchpad.net/deluge-team/ubuntu intrepid main
deb-src http://ppa.launchpad.net/deluge-team/ubuntu intrepid main
prest@prest-OptiPlex-GX270:~$ ls /etc/apt/sources.list.d/
```

Why are you using the intrepid ppa for launch pad? AFAIK Intrepid is no longer maintained.

Kind regards

---

### Post by Verbeck on 2011-01-04
run [I]gksu gedit /etc/apt/sources.list
[/I]and delete the last 8 lines and save the file. 
(as [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") pointed out, intrepid is no longer officially supported)

also run the 2nd command in my previous post

---

### Post by matt_symes on 2011-01-04
Hi

Have a read of this.

[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)

Kind regards

---

### Post by captaincornwall on 2011-01-04
Awesome that worked. Thanks so much.

why did that happen and what did the code do. Just so I can learn a bit. Know very little about coding.

No idea why I'm using intrepid ppa for launch pad or even what it does or how to change it.

Really sorry recent converter from bloody Windows which I fear has made me thick as far as computing is concerned. Still getting my head around Linux and the differences. Still cant fathom what it uses instead of .exe files and the insane why programes are stored. Can't seem to find the .exe equivalent for firestarter and Clam to put them in my start up.

thanks again guys:)

---

### Post by matt_symes on 2011-01-04
Hi

Intrepid is an old version of Ubuntu that is no longer supported.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Don't feel thick or stupid. You're not. You're learning. There is a huge difference

> Can't seem to find the .exe equivalent for firestarter and Clam to put them in my start up.

Don't bother with a firewall if i were you. You do not really need one if you are not starting any open services on the desktop version. However if you do want one have a look at

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

as a front end to net filter and iptables.

As for anti virus... Anti virus pros and cons and clamAV

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

> firestarter and Clam to put them in my start up.

On mine....

```
 matthew@matthew-laptop:~/linux-2.6.32/init$ ps aux | grep -i clam
clamav   22511  0.0  0.0  12756  1156 ?        Ss   12:51   0:00 /usr/bin/freshclam -d --quiet 
```


Not quite sure what you mean by startup. Both will run at startup if installed and enabled.

Kind regards

---

