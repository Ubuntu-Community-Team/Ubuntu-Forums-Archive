---
title: "E:Type 'usage:' is not known on line 56 in source list /etc/apt/sources.list, E:The l"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2010-09-14
Hello,

I'm fairly new to Ubuntu, but not completely un-geeky.

When I try to search for an application in the software center I get no results. Furthurmore I have this alert on my top panel; when I double click on it I go to the update manager with the following error:
> 
 Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'usage:' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'I also cannot install applications through the terminal. 

I tried finding a fix, but it seems there is no generic remedy. Any help is appreciated.

---

### Post by gmargo on 2010-09-14
Please post the content of your **/etc/apt/sources.list** file; the problem will probably be clear.

---

### Post by Light Knight 22 on 2010-09-14
> #deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
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
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

Thanks!

---

### Post by snowpine on 2010-09-14
/etc/apt/sources.list is an important system file, and you should be careful editing it!

Apparently there is an error on line 56. If you can post the contents of the file using the following command, we can try to help you sort it out. :)

```
cat /etc/apt/sources.list
```

(edit) Too slow! Looking at the file, I would recommend deleting the following lines:

```
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
username|#uid] file ... 
```

To edit the file as root (be very, very careful!) use:

```
gksu gedit /etc/apt/sources.list
```

or if you prefer the terminal:

```
sudo nano /etc/apt/sources.list
```

---

### Post by Light Knight 22 on 2010-09-14
Thank you very much! It's working better so far.

As a last question, how did source list get edited? I didn't touch it.

---

### Post by snowpine on 2010-09-15
> **Light Knight 22 said:**
> Thank you very much! It's working better so far.

As a last question, how did source list get edited? I didn't touch it.

You're welcome! **I** certainly didn't edit it, so your guess is as good as mine. :)

---

