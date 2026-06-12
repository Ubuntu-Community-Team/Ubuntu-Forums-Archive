---
title: "Bug in synaptic manager"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by dr.anandravi on 2009-04-20
Hi!
while opening the Synaptic manager this message comes;
Report this bug and include this:
E:Type '.' is not known on line 2 in source list /etc/apt/sources.list.d/pidgin-ppa.list, E:The list of sources could not be read.'
 And after closing this message the synaptic manager window automatically goes off.thus I am unable to to open that.
Please suggest what to do?

---

### Post by gandaran on 2009-04-20
> **dr.anandravi said:**
> Hi!
while opening the Synaptic manager this message comes;
Report this bug and include this:
E:Type '.' is not known on line 2 in source list /etc/apt/sources.list.d/pidgin-ppa.list, E:The list of sources could not be read.'
 And after closing this message the synaptic manager window automatically goes off.thus I am unable to to open that.
Please suggest what to do?
remove the line from /etc/apt/sources.list.d/pidgin-ppa.list, something is not right with this repository you added.
run in terminal
> sudo gedit /etc/apt/sources.list

---

### Post by Paqman on 2009-04-20
> **gandaran said:**
> remove the line from /etc/apt/sources.list.d/pidgin-ppa.list, something is not right with this repository you added.
run in terminal

Please use gksudo with graphical apps. The command should be:
```

gksu gedit /etc/apt/sources.list 

```

---

### Post by bumanie on 2009-04-20
The message is most likely not a bug. There is something wrong with line 2 of the /etc/apt/sources list. If you are not sure what to do, post a copy of the list. You should use > gksudo gedit /etc/apt/sources.list gksudo is used when super user function is used in graphical mode.

Modified : Forgot the gedit

---

### Post by Paqman on 2009-04-20
Ahem, you completely sure about that command bumanie? ;)

EDIT: That's the one!

---

### Post by dr.anandravi on 2009-04-21
Thanks for your intrest in my problem.I am sending the full source list, please suggest what to do.The Add/Remove programe is also not responding.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by nandemonai on 2009-04-21
Also the contents of the /etc/apt/sources.list.d/pidgin-ppa.list file please as that is where the error lies.

Your /etc/apt/sources.list file is fine.

You've likely made a simple error while adding this 3rd party repository (Which isn't always a great idea in my humble opinion).

---

### Post by gandaran on 2009-04-21
> **nandemonai said:**
> Also the contents of the /etc/apt/sources.list.d/pidgin-ppa.list file please as that is where the error lies.

Your /etc/apt/sources.list file is fine.

You've likely made a simple error while adding this 3rd party repository (Which isn't always a great idea in my humble opinion).
I just went through the same problem, any one using [this guide]("http://www.pidgin.im/download/ubuntu/") will land up with this problem, the correct guide for installing the ppa repo is [this one]("https://launchpad.net/~pidgin-developers/+archive/ppa")
the ppa repo is not showing on the sources.list so theres no way you can remove it and also for some reason it wont remove by using the system » administration » software sources, the only way to fix it is by editing system » administration » software sources » third party applications » pidgin ppa 
the correct entries should read, edit the following
url:------------------http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu
distribution:-------intrepid or hardy is that is your case
components: -----main  
problem fixed.

---

### Post by dr.anandravi on 2009-04-22
> **nandemonai said:**
> Also the contents of the /etc/apt/sources.list.d/pidgin-ppa.list file please as that is where the error lies.

Your /etc/apt/sources.list file is fine.

You've likely made a simple error while adding this 3rd party repository (Which isn't always a great idea in my humble opinion).

A lot of thanks.I opened the /etc/apt/sources.list.d/pidgin-ppa.list and removed the all text.Problem resolved.
Thanks again.

---

