---
title: "Problem installing ubuntu intrepid"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-25
IM USING HARDY HERON,,and i tried installing intrepid thourhg hte updat manager,,but i get an error, that wont let me install it...i tried
sudo apt-get install -f cus it tells me to,,but i get this how can i upgrade and fix all these errors and problems???

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libhtml-parser-perl: Depends: perlapi-5.10.0
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.3 is installed
  uuid-dev: Depends: libuuid1 (= 1.41.3-1ubuntu1) but 1.40.8-2ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by itsvan on 2009-01-25
it says my software indez is broken

---

### Post by taurus on 2009-01-25
Then why don't you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by itsvan on 2009-01-25
#

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

# Wine

---

### Post by taurus on 2009-01-25
I assume that is the whole /etc/apt/sources.list.

What happens when you run these commands from a terminal?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by itsvan on 2009-01-25
i get this



Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libhtml-parser-perl: Depends: perlapi-5.10.0
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.3 is installed
  uuid-dev: Depends: libuuid1 (= 1.41.3-1ubuntu1) but 1.40.8-2ubuntu2 is installed
E: Unmet dependencies. Try using -f.

---

### Post by taurus on 2009-01-25
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by itsvan on 2009-01-25
when i tru the first command this shows up,,doesnt seem good


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libhtml-parser-perl: Depends: perlapi-5.10.0
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.3 is installed
  uuid-dev: Depends: libuuid1 (= 1.41.3-1ubuntu1) but 1.40.8-2ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

