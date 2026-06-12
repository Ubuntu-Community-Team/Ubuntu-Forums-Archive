---
title: "Adding repositories"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-26
Tried in another thread but no responses so thought I'd try it here.

Had a bunch of problems and "downgraded" from 10.04 to 9.10 and was wondering if anybody knew if the list of repositories given in the Ubuntu Karmic Koala Bible were still available and correct? Is there somewhere I can find the current, active, list of repositories for 9.10?

Thanks for the assist. The "Bible" is great, just want to make sure it's not outdated.

---

### Post by -humanaut- on 2010-05-26
open a terminal type: cat /etc/apt/sources.list

and post back.

---

### Post by flyfishingphil on 2010-05-26
> **-humanaut- said:**
> open a terminal type: cat /etc/apt/sources.list

and post back.
Did the terminal. Here's what came back:

[I]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

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
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse[/I]

Is this all that is needed? I'm trying to get my Sony Ericsson W760i cell, Magellan Explorist 400 GPS and a few programs to work. WINE doesn't seem to work with much but games, from what I've accomplished with it, and waiting on XP Pro arrival before I do the VBox.

---

### Post by flyfishingphil on 2010-05-27
bump

---

### Post by oldos2er on 2010-05-27
Do you get any errors when you run **sudo apt-get update** ?

---

### Post by flyfishingphil on 2010-05-27
> **oldos2er said:**
> Do you get any errors when you run **sudo apt-get update** ?
Just did it and here is all I note for "errors" in the listing:

[I]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

---

### Post by oldos2er on 2010-05-27
Go into your Software Sources (System, Administration, Software Sources) and under the 'Other Software' tab uncheck the PPA repositories, and hopefully that will get rid of the errors.

---

### Post by flyfishingphil on 2010-05-27
> **oldos2er said:**
> Go into your Software Sources (System, Administration, Software Sources) and under the 'Other Software' tab uncheck the PPA repositories, and hopefully that will get rid of the errors.
Did that and ran sudo apt-get update and received no errors. Still wondering though if there are any more repositiories I need to add and, if so, are the ones listed in the Ubuntu Karmic Koala Bible still active and current? (I'd add in the list but that would take a long time to enter and lots of space too.)

---

### Post by wojox on 2010-05-27
> **flyfishingphil said:**
> Did that and ran sudo apt-get update and received no errors. Still wondering though if there are any more repositiories I need to add and, if so, are the ones listed in the Ubuntu Karmic Koala Bible still active and current? (I'd add in the list but that would take a long time to enter and lots of space too.)

I looked at Karmic Bible and they should all be up to date and you should be able to install them.

```

#
# Ubuntu Karmic Koala 9.10 Repositories, from the_guv @ http://guvnr.com
#
#
# Ubuntu Karmic
#
deb http://archive.ubuntu.com/ubuntu karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe
multiverse
deb http://archive.ubuntu.com/ubuntu karmic-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu karmic-updates main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe
multiverse
#
# Canonical Commercial
#
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner
#
# System Tools
#
# Ubuntu Tweak
# Must-have Ubuntu configuration tool .. http://ubuntu-tweak.com/about
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main
#
# Productivity
#
# Gnome-do
# Mac-like desktop apps dock for improved productivity .. http://do.davebsd.com/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
# Gnome-Globalmenu
# OS X-style global menu .. http://code.google.com/p/gnome2-globalmenu/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ubuntu karmic main
# Nautilus-dropbox
# File syncing online & across machines, with 2Gb space for free ..
http://www.getdropbox.com/
deb http://linux.getdropbox.com/ubuntu karmic main
#
# Computer Graphics & Themes
#
# Compiz-Fusion
# Improved usability with jazzed up graphics .. http://www.compiz-fusion.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main
# Gnome Icon Theme
# Nice desktop graphics .. http://www.gnome-look.org/content/show.php/GNOME-
colors?content=82562
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
# Project Bisigi Themes
# Strikingly beautiful Gnome themes .. http://www.bisigi-project.org/?lang=en
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
#
# Web browsers
#
# Chromium Browser
# Open-source Webkit browser, for testing Safari and Chrome .. http://dev.chromium.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
# Epihany
# Another Webkit browser, for testing Safari and Chrome ..
http://projects.gnome.org/epiphany/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D9A3C5B
deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main
deb-src http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main
# Firefox
# Gecko browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
# deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main
# This gets latest beta .. for addon conpatability, add bolean to about:config:
extensions.checkCompatibility
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
# deb http://dl.google.com/linux/deb/ stable non-free
# Opera
# Presto browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 033431536A423791
deb http://deb.opera.com/opera/ stable non-free
#
# Communication
#
# Pidgin
# Multi-client instant messenger .. http://www.pidgin.im/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
#
# Media
#
# Medibuntu
# Multimedia, entertainment and other distractions .. http://www.medibuntu.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free
# VLC Player
# Media player, well decked with codecs .. http://www.videolan.org/vlc/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
#
# Extend with Web Development Packages Tools
#
# Drizzle
# Modular relational db optimised for Cloud and Net apps, a MySQL fork ..
https://launchpad.net/drizzle
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
#
# Graphics Tools
#
# Shutter
# Feature-rich screenshot program .. http://shutter-project.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
#
# Windows/OS Emulators, Translators, Virtualizers, all that
#
# PlayOnLinux
# Run Windows wares and games .. http://www.playonlinux.com/en
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://deb.playonlinux.com/ karmic main
# Setup a Virtual OS with Virtualbox (sure beats a dual-boot!)
# Virtualization software for guest OSes .. http://www.virtualbox.org
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
# Wine
# Run Windows apps .. http://www.winehq.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 58403026387EE263
deb http://wine.budgetdedicated.com/apt karmic main
#
# Package Management
#
# Subversion
# Software versioning .. http://subversion.tigris.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
#
# Other Applications
#
# Google
# Picassa, Google Desktop and maybe other stuff .. er, google it!
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
##########################################################################

```

```
sudo aptitude update
```

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 991E6CF92D9A3C5B
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com EF4186FE247510BE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB


```

```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```

---

### Post by flyfishingphil on 2010-05-27
> **wojox said:**
> I looked at Karmic Bible and they should all be up to date and you should be able to install them.

```

#
# Ubuntu Karmic Koala 9.10 Repositories, from the_guv @ http://guvnr.com
#
#
# Ubuntu Karmic
#
deb http://archive.ubuntu.com/ubuntu karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu karmic-backports main restricted universe
multiverse
deb http://archive.ubuntu.com/ubuntu karmic-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu karmic-updates main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe
multiverse
#
# Canonical Commercial
#
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner
#
# System Tools
#
# Ubuntu Tweak
# Must-have Ubuntu configuration tool .. http://ubuntu-tweak.com/about
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main
#
# Productivity
#
# Gnome-do
# Mac-like desktop apps dock for improved productivity .. http://do.davebsd.com/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
# Gnome-Globalmenu
# OS X-style global menu .. http://code.google.com/p/gnome2-globalmenu/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ubuntu karmic main
# Nautilus-dropbox
# File syncing online & across machines, with 2Gb space for free ..
http://www.getdropbox.com/
deb http://linux.getdropbox.com/ubuntu karmic main
#
# Computer Graphics & Themes
#
# Compiz-Fusion
# Improved usability with jazzed up graphics .. http://www.compiz-fusion.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main
# Gnome Icon Theme
# Nice desktop graphics .. http://www.gnome-look.org/content/show.php/GNOME-
colors?content=82562
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
# Project Bisigi Themes
# Strikingly beautiful Gnome themes .. http://www.bisigi-project.org/?lang=en
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
#
# Web browsers
#
# Chromium Browser
# Open-source Webkit browser, for testing Safari and Chrome .. http://dev.chromium.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
# Epihany
# Another Webkit browser, for testing Safari and Chrome ..
http://projects.gnome.org/epiphany/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D9A3C5B
deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main
deb-src http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main
# Firefox
# Gecko browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
# deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main
# This gets latest beta .. for addon conpatability, add bolean to about:config:
extensions.checkCompatibility
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
# deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
# deb http://dl.google.com/linux/deb/ stable non-free
# Opera
# Presto browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 033431536A423791
deb http://deb.opera.com/opera/ stable non-free
#
# Communication
#
# Pidgin
# Multi-client instant messenger .. http://www.pidgin.im/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
#
# Media
#
# Medibuntu
# Multimedia, entertainment and other distractions .. http://www.medibuntu.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free
# VLC Player
# Media player, well decked with codecs .. http://www.videolan.org/vlc/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
#
# Extend with Web Development Packages Tools
#
# Drizzle
# Modular relational db optimised for Cloud and Net apps, a MySQL fork ..
https://launchpad.net/drizzle
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
#
# Graphics Tools
#
# Shutter
# Feature-rich screenshot program .. http://shutter-project.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
#
# Windows/OS Emulators, Translators, Virtualizers, all that
#
# PlayOnLinux
# Run Windows wares and games .. http://www.playonlinux.com/en
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://deb.playonlinux.com/ karmic main
# Setup a Virtual OS with Virtualbox (sure beats a dual-boot!)
# Virtualization software for guest OSes .. http://www.virtualbox.org
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
# Wine
# Run Windows apps .. http://www.winehq.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 58403026387EE263
deb http://wine.budgetdedicated.com/apt karmic main
#
# Package Management
#
# Subversion
# Software versioning .. http://subversion.tigris.org/
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
#
# Other Applications
#
# Google
# Picassa, Google Desktop and maybe other stuff .. er, google it!
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
##########################################################################

```

```
sudo aptitude update
```

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 991E6CF92D9A3C5B
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com EF4186FE247510BE
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB


```

```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```
Thanks for grabbing those wojox! I printed a copy of the bible and figured I'd just have to set down and start typing to get them all in. Now I can highlite, copy and past from the list you grabbed making it much easier.

Thanks again. Don't really know if I need them but would rather have them avaiable if needed than have to chase one down.

---

