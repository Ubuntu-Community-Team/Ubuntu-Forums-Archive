---
title: "Malformed Line in sources.list"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Pushpalanka on 2011-01-21
**:Malformed line 46 in source list /etc/apt/sources.list(dist parse)**
I get the above error when I try to install a .deb file by double clicking. I am thankful to any help on this.

---

### Post by Elfy on 2011-01-21
Best to start your own threads - I moved this to it's own thread.

If you are not happy following the instruction in the thread you added on to.

Open the file and paste the contents here please. From a terminal (Apps - Accessories - Terminal) run this 

```
gedit /etc/apt/sources.list
```

---

### Post by Pushpalanka on 2011-01-21
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://io.archive.ubuntu.com/ubuntu/](http://io.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


This is what I got for the above terminal command

---

### Post by howefield on 2011-01-21
Use the command

```
gksudo gedit /etc/apt/sources.list
```

And remove the last line, the one that looks like this

```
deb http://archive.canonical.com/lucid partner
```

Save, reload your software sources and try again.

---

### Post by matt_symes on 2011-01-21
Hi

Remove this line

```
deb http://archive.canonical.com/lucid partner
```

It's the last line in your sources.list file.

EDIT: Beaten to it ;)

Kine regards

---

### Post by Elfy on 2011-01-21
Remove it - not sure about line 45 either.

Open the file to edit as root

```
gksudo gedit /etc/apt/sources.list
```

Put a # at the beginning of the line.

Save, close and update

```
sudo apt-get update
```
If you get a line 45 error, try

```
deb http://archive.canonical.com/ubuntu lucid partner
```

---

### Post by Pushpalanka on 2011-01-21
It worked after deleting last line. Thank you all. :)

---

