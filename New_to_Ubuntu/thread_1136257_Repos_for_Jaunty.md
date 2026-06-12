---
title: "Repos for Jaunty"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Swatfoot on 2009-04-24
I just upgraded to jaunty from 8.10 and my synaptic is very empty so I was wondering if I need to add to the sources to have access to them.

---

### Post by Rocket2DMn on 2009-04-24
You can check what is enabled under System->Administration->Software Sources.  You can also post your sources.list file for us to look at - /etc/apt/sources.list

---

### Post by Swatfoot on 2009-04-24
Here is sources.list



# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty universe
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty multiverse
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security main restricted
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security universe
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) jaunty-security multiverse

---

### Post by Rocket2DMn on 2009-04-24
Looks OK to me, did you switch mirrors after your upgrade?

Please run
```
sudo apt-get update
sudo apt-get upgrade
```
That will read down the list and perform any upgrades that are pending.  If you switched to this mirror after upgrading, it's possible that they are not fully synced yet.

---

### Post by Swatfoot on 2009-04-24
Ok this worked.

sudo apt-get update
sudo apt-get upgrade

yes i did changed to mirror help keep the load off man servers,was suggested to me when I started with hardy.Thanks for the help!

---

