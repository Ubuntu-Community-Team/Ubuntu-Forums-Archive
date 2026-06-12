---
title: "updating error"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by libihero on 2009-10-17
what does this error mean and how do i fix it?
GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures coul
dn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sandyd on 2009-10-17
> **libihero said:**
> what does this error mean and how do i fix it?
GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures coul
dn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
run this
```

wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```
then 
```

gksudo /etc/apt/sources.list

```
comment out the line that has "cdrom" somewhere in it.
then
```

sudo apt-get update

```

---

### Post by MelDJ on 2009-10-18
you must add the GPG key for opera. add it by following this: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

and you must remove the cdrom from your sources list. other than the way shown by the above poster, you can go to software sources and uncheck the cdrom

---

### Post by libihero on 2009-12-11
any help with this one too? 
```
W: Duplicate sources.list entry http://archive.ubuntu.com karmic/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com karmic/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://dl.google.com stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

i ran sudo apt-get update and it keeps coming up
thanks :)

---

### Post by ukripper on 2009-12-11
can you post your sources.list here.

```
gedit /etc/apt/sources.list
```

---

### Post by libihero on 2009-12-11
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

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

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu) karmic main
# deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main

---

### Post by joes7 on 2009-12-18
Re-install.

---

### Post by Extract_Here on 2009-12-18
I would have to go to a terminal update and if that doesnt work then go for a re-installation

---

### Post by libihero on 2009-12-18
woah reinstall? its that bad?
i mean it actually hasnt come up anymore..... but did something break?

---

### Post by sandyd on 2009-12-20
Can you post the output of
```
ls /etc/apt/sources.list.d
```

---

### Post by libihero on 2009-12-20
i already did, see my previous two posts :)

---

### Post by libihero on 2009-12-20
it did stop tho, but i just got worried cuz the last two guys said i had to reinstall and im scared i mighta really messed something up

---

### Post by ukripper on 2009-12-21
> **libihero said:**
> it did stop tho, but i just got worried cuz the last two guys said i had to reinstall and im scared i mighta really messed something up

People who told you to re-install ubuntu again was bit drastic and stupid measure, there is no such need. It was just duplicate entries in your apt sources, nothing to worry about. It has no impact on your system usage/settings or your data. This problem can be corrected by finding all the duplicate sources in /etc/apt/sources.list and put **```
# 
```**(hash) in front of them, so that only one entry is remaining for the sources added in your sources.list.

apt-get update might have corrected that problem for you. If it happens again just post your sources.list here again then someone will identify the duplicates for you.

---

