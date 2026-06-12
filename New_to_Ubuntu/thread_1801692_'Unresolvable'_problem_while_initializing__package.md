---
title: "'Unresolvable' problem while initializing  package information"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by eduardo saxel on 2011-07-10
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '123456' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

What to do?

---

### Post by wojox on 2011-07-10
Copy and paste your sources.list up here.

---

### Post by eduardo saxel on 2011-07-10
How to do it?

---

### Post by eduardo saxel on 2011-07-10
Oh!


/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-chrome.list.save
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save

This?

---

### Post by wojox on 2011-07-10
Almost. :P

Ctrl+Alt+T

```
cat /etc/apt/sources.list
```

---

### Post by eduardo saxel on 2011-07-10
Maybe this...

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

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
123456
deb [http://kondr.ic.cz/deb](http://kondr.ic.cz/deb) lucid main
deb [http://kondr.ic.cz/deb](http://kondr.ic.cz/deb) lucid main

---

### Post by wojox on 2011-07-10
That's it. Run:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

```
gksudo gedit /etc/apt/sources.list
```

Remove the [COLOR="Red"]123456[/COLOR] near the bottom and save and update.

---

### Post by eduardo saxel on 2011-07-10
Oh! I see. Line 54 of the source.list: 123456

How to 'erase' that?

---

### Post by wojox on 2011-07-10
> **wojox said:**
> That's it. Run:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

```
gksudo gedit /etc/apt/sources.list
```

Remove the [COLOR="Red"]123456[/COLOR] near the bottom and save and update.

This ^^

---

### Post by eduardo saxel on 2011-07-11
That's it. Thank you very much

---

