---
title: "&quot;Could not initialize the package information&quot;-Error pls help"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by lamboram on 2008-12-09
Could not initialize the package information
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'echo' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

this was error i got yesterday wen i tried to follow some internet tips on installing AWN thru terminal..am extremely new to linux[ubuntu 8.10] one of my friend told me abt this forum..pls help..should i reinstall ubuntu by formattim\ng..or is there a solution.the thing is that my system is not updating and i am not able to install or uninstall anything..pls help
thanks in advance
Ramesh-India

---

### Post by binbash on 2008-12-09
cat /etc/apt/sources.list

paste the all output here.

---

### Post by lamboram on 2008-12-09
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main' 
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

---

### Post by binbash on 2008-12-09
remove those lines : 


echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

---

### Post by lamboram on 2008-12-09
how should i remove it..and when i selct those lines and press del in terminal its not respondin lik its beepin tellin that am not valid to delete it..

---

### Post by binbash on 2008-12-09
sudo gedit /etc/apt/sources.list

dont forget to save after removing

---

### Post by lamboram on 2008-12-09
thanks mate...i have no word to thank u..u r diamond mate..:p

---

