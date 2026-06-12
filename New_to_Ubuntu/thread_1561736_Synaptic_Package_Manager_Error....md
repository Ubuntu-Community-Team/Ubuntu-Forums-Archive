---
title: "Synaptic Package Manager Error..."
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Sojikari on 2010-08-26
Recently, I installed Playonlinux. Not that I've gotten it to work, mind you. There is apparently an update available, but I've got a circular argument running.

Playonlinux's update package <i>downloaded</i> without an issue. It's Synaptic Package Installer, which has gone completely loopy since I installed playonlinux. Here's what I get:


E: Type '--2010-08-24' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Which brought up an interesting few problems.
1) /etc/apt/sources.list.d/playonlinux.list is a Root User file, and I can't figure out how to fix/edit/delete this file.
2) I can't install <i>anything</i> using Synaptic Package manager, without this file clearing itself up.

Any, and all assistance is appreciated. Thanks

-n00b Ubuntu user

---

### Post by arochester on 2010-08-26
Look at your sources list. In a Terminal use the command: gksudo gedit /etc/apt/sources.list

Copy and paste the result here.

Line one is suspect, but need to see things first before advising you.

---

### Post by Sojikari on 2010-08-26
In order: Log-in((Sudo command used))

Opened gedit

gedit opened the following file:

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

#Eternal Lands package repository
deb [http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu) lucid main

---

### Post by arochester on 2010-08-26
Strangely there is no mention of any PlayOnLinux repository in your list. I have just installed it and it is in my list.

It might sound daft, but I would TRY rebooting and running
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
...any error messages nor?

---

### Post by Sojikari on 2010-08-26
All three get the following:

E: Type '--2010-08-24' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.

Edit: Off to work. Back in 10 hours.

---

### Post by coffeecat on 2010-08-26
> **Sojikari said:**
> All three get the following:

E: Type '--2010-08-24' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.

The problem is in /etc/apt/sources.list.d/playonlinux.list, **not** in /etc/apt/sources.list. Can you post the contents of /etc/apt/sources.list.d/playonlinux.list ?

---

### Post by Sojikari on 2010-08-26
--2010-08-24 13:48:35--  [http://deb.playonlinux.com/playonlinux_intrepid.list](http://deb.playonlinux.com/playonlinux_intrepid.list)
Resolving deb.playonlinux.com... 91.121.5.64
Connecting to deb.playonlinux.com|91.121.5.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 46 [text/plain]
Saving to: `playonlinux_intrepid.list'

     0K                                                       100% 1.29M=0s

2010-08-24 13:48:36 (1.29 MB/s) - `playonlinux_intrepid.list' saved [46/46]

--2010-08-24 13:48:36--  [http://sudo/](http://sudo/)
Resolving sudo... failed: Name or service not known.
wget: unable to resolve host address `sudo'
--2010-08-24 13:48:36--  [http://apt-get/](http://apt-get/)
Resolving apt-get... failed: Name or service not known.
wget: unable to resolve host address `apt-get'
--2010-08-24 13:48:36--  [http://update/](http://update/)
Resolving update... failed: Name or service not known.
wget: unable to resolve host address `update'
FINISHED --2010-08-24 13:48:36--
Downloaded: 1 files, 46 in 0s (1.29 MB/s)

---

### Post by Sojikari on 2010-08-27
That is the file. :(

I don't get it.

---

### Post by Elfy on 2010-08-27
It's wrong, in a terminal do this to remove the old list. Sources list should only have deb or deb-src lines enabled.

```
sudo rm /etc/apt/sources.list.d/playonlinux.list
```

Then start again from the playonlinux download page - [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

---

### Post by Sojikari on 2010-08-27
I <3 you.

It works perfectly now. :D

Thank you!!! <3

---

