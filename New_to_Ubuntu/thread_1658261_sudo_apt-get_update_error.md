---
title: "sudo apt-get update error"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by lbarnes on 2011-01-02
I need help removing this error:
```
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_sevenmachines_flash_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
lennon@lennon-HP-HDX-16-Notebook-PC:~$ 

```

Here is my sources.list
```

```# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick main restricted
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates main restricted
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick universe
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick universe
deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates universe
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick multiverse
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick multiverse
deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates multiverse
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security main restricted
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security main restricted

deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security universe
deb-src [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-security universe

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib

deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /

deb [http://mirrors.pavlovmedia.net/ubuntu/](http://mirrors.pavlovmedia.net/ubuntu/) maverick-backports restricted main multiverse universe

---

### Post by gmargo on 2011-01-02
You probably have some additional sources in the **/etc/apt/sources.list.d/** directory.

---

### Post by blazemore on 2011-01-02
Hit alt_f2, type "gksu software-properties-gtk" without the quotes and hit Enter.

Type your password and hit Enter.

Go to Other Software.
This lists all the repositories you have added.
Here you can remove the duplicate entry, as it will be more obvious.

The reason it's not in your sources.list is that, unlike Debian, Ubuntu stores ppa information in the directory /etc/apt/sources.list.d/ not in sources.list

---

### Post by lbarnes on 2011-01-02
Yeah, I found it in the sources.list.d folder.  One of the files in there had a dubplicate line, thx guys.

---

