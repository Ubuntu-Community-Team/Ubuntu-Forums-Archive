---
title: "could not mark all packages for installation"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by MelDJ on 2009-08-04
i am trying to install anjunta through synaptic . When i press mark for installation this comes along : 
anjuta:
 Depends: libapr1  but it is not installable
 Depends: libaprutil1  but it is not installable
 Depends: libdevhelp-1-0 (>=0.14) but it is not installable
 Depends: libgbf-1-1 but it is not going to be installed
 Depends: libgdl-1-0  but it is not installable
 Depends: libgdl-gnome-1-0  but it is not installable
 Depends: libgladeui-1-7  but it is not installable
 Depends: libsvn1 (>=1.4) but it is not installable
 
what does it mean??:confused:

---

### Post by any.linux12 on 2009-08-04
update your packages and try again...

---

### Post by MelDJ on 2009-08-04
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

:(

---

### Post by drs305 on 2009-08-04
Run this command to add the key and remove the error message:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4874D3686E80C6B7
```

---

### Post by MelDJ on 2009-08-04
i ran the command and ran sudo apt-get update again and did not get the error message. I went to synaptic, reloaded and tried to install anjunta again but the error in my 1st post is still coming up. Any idea what to do?:confused:

---

### Post by philinux on 2009-08-04
Did you run 

sudo apt-get upgrade

?

---

### Post by harry2006 on 2009-08-04
> **MelDJ said:**
> i ran the command and ran sudo apt-get update again and did not get the error message. I went to synaptic, reloaded and tried to install anjunta again but the error in my 1st post is still coming up. Any idea what to do?:confused:
i guess apt-get update should have fixed the problem...
are you still facing the problem?

---

### Post by MelDJ on 2009-08-04
> **philinux said:**
> Did you run 

sudo apt-get upgrade

?

no..but i did apt-get update

---

### Post by credobyte on 2009-08-04
And what if you do it via terminal ?

```
sudo apt-get install anjuta
```

---

### Post by MelDJ on 2009-08-04
> **credobyte said:**
> And what if you do it via terminal ?

```
sudo apt-get install anjuta
```

i get this...

 The following packages have unmet dependencies:
  anjuta: Depends: libapr1 but it is not installable
          Depends: libaprutil1 but it is not installable
          Depends: libdevhelp-1-0 (>= 0.14) but it is not installable
          Depends: libgbf-1-1 but it is not going to be installed
          Depends: libgdl-1-0 but it is not installable
          Depends: libgdl-gnome-1-0 but it is not installable
          Depends: libgladeui-1-7 but it is not installable
          Depends: libsvn1 (>= 1.4) but it is not installable
E: Broken packages

pressing fix broken packages in synaptic does not help as i get the same message..

---

### Post by oldos2er on 2009-08-04
> **MelDJ said:**
>  pressing fix broken packages in synaptic does not help as i get the same message..

 Can you post the output of ```
cat /etc/apt/sources.list
``` ?

---

### Post by MelDJ on 2009-08-05
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) hardy restricted universe
deb-src [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) hardy multiverse
deb-src [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) hardy main
# deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) hardy main #gnome-do
# deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) hardy main #gnome-globalmenu
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free #virtualbox
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #medibuntu
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) hardy main #xbmc
deb [http://ppa.launchpad.net/googlegadgets/ppa/ubuntu](http://ppa.launchpad.net/googlegadgets/ppa/ubuntu) hardy main #google-gadgets
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #google
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) hardy main
# deb [http://download.tuxfamily.org/swiftweasel](http://download.tuxfamily.org/swiftweasel) hardy multiverse #swiftweasel
# deb [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu) hardy main
# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) hardy main #shutter
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) hardy main #compiz-fusion
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main universe multiverse restricted
deb [http://ftp.hostrino.com/pub/ubuntu/archive/](http://ftp.hostrino.com/pub/ubuntu/archive/) hardy-updates restricted multiverse universe

---

### Post by MelDJ on 2009-08-05
when i try to install miro, this comes 

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  miro: Depends: libboost-python1.34.1 (>= 1.34.1-2.1) but it is not installable
        Depends: libxine1 (>= 1.1.8) but it is not installable
        Depends: libxine1-x but it is not installable
        Depends: python-gnome2-extras (>= 2.14.0-2) but it is not installable
        Depends: python-pysqlite2 but it is not installable

help...:(

---

### Post by drs305 on 2009-08-05
When I look at your sources.list I see "main" for a lot of the third party repositories (launchpad, etc) but didn't see any of the standard repositories. 

Do you have the *main, restricted, multiverse and universe* repositories enabled in the Ubuntu Software tab: Synaptic, Settings, Respositories? It doesn't appear you do. Unless you have a specific reason for not doing so, these are normally enabled. Once you have selected them, hit "Reload" and try to run your commands again.

---

### Post by MelDJ on 2009-08-05
WORKS! thanks a lot kawan!

---

