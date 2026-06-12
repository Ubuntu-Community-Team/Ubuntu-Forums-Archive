---
title: "lsb-core refuses installation"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by okkie on 2011-02-09
Ubuntu maverick.Googleearth can now successfully run on 10.10 providing lsb-core is installed.
arrached is a screenshot of error I get during installation.Can anyone please tell me what to do to to get lsb-core installed? The suggested action doesn't work.

---

### Post by okkie on 2011-02-09
Sorry for that ,here is a better photo

---

### Post by cavh on 2011-02-09
run ```
sudo apt-get update
``` first to update the list of packages available in the repositories, then ```
sudo apt-get install lsb-core
```

---

### Post by okkie on 2011-02-11
Thanks for your time.Exactly the same error comes up

---

### Post by cavh on 2011-02-14
There is a space between **ubuntu/** and **maverick** in your URL, which is wrong. 

Type this command into a terminal window to edit your sources.list file and remove the offending space:

```
gksudo gedit /etc/apt/sources.list &
```

and then run the commands I gave earlier to update your package information and try installing lsb-core again.

EDIT - ignore that (my mistake), please post the content of /etc/apt/sources.list so I can see what you have.

---

### Post by okkie on 2011-02-18
> **cavh said:**
> There is a space between **ubuntu/** and **maverick** in your URL, which is wrong. 

Type this command into a terminal window to edit your sources.list file and remove the offending space:

```
gksudo gedit /etc/apt/sources.list &
```

and then run the commands I gave earlier to update your package information and try installing lsb-core again.

EDIT - ignore that (my mistake), please post the content of /etc/apt/sources.list so I can see what you have.

sorry for only coming back now but things have been a bit hectic.Thanks for your help.
If I type /etc/apt/sources.list in root or normal terminal it says permission is denied.Am I doing it incorrectly? Just to give you a bit of background,everything revolves around the installation of googleearth which I use in my line of business.I have now for three years and four complete system installations  been trying to get it going with no luck.
Thanks.

---

### Post by okkie on 2011-02-18
I got hold of the sources list:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by okkie on 2011-03-05
finally installed the normal way.

---

### Post by shezars on 2012-05-16
Is your problem is solved?
How,

thanks ](*,)

---

