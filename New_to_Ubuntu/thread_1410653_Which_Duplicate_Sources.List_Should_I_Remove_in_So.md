---
title: "Which Duplicate Sources.List Should I Remove in Software Sources?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-19
Hello everyone,

I'm sure this is abundantly apparent, but I am not sure which Medibuntu source I should remove in Software Sources, so as to not have duplicates as seen in the screenshot of my sudo apt-get update. If you could tell me which to remove, I would be very appreciative.

Thank you.

Please see the screenshots below:

---

### Post by nhasian on 2010-02-19
you will need to post the output of the following command:

```
cat /etc/apt/sources.list
```

---

### Post by Mustard on 2010-02-19
I would say either one really.  Leave the 'source' on, but take your pick with regards to the other choices.  They are both connecting to 'free nonfree'

---

### Post by mikodo on 2010-02-19
> **nhasian said:**
> you will need to post the output of the following command:

```
cat /etc/apt/sources.list
```

EDIT:  Say, I don't know what uncomment the following two lines here means, and what purpose it serves to accomplish that.

Thanks. As requested see below:

mikodo@mikodo-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted universe multiverse main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted multiverse universe main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
mikodo@mikodo-desktop:~$

---

### Post by plucky on 2010-02-19
You have two entries for Medibuntu.One is in your /etc/apt/sources.list.
The other one is probably in /etc/apt/sources.list.d/medibuntu.list.

Use

```
gksudo gedit /etc/apt/sources.list
```

and put a **#** in front of this line ```
deb http://packages.medibuntu.org/ karmic free non-free
```

Then from a terminal ```
sudo apt-get update
``` and see if you still get the same error.

Good Luck

---

### Post by mikodo on 2010-02-19
> **plucky said:**
> You have two entries for Medibuntu.One is in your /etc/apt/sources.list.
The other one is probably in /etc/apt/sources.list.d/medibuntu.list.

Use

```
gksudo gedit /etc/apt/sources.list
```

and put a **#** in front of this line ```
deb http://packages.medibuntu.org/ karmic free non-free
```

Then from a terminal ```
sudo apt-get update
``` and see if you still get the same error.

Good Luck

Thank you for the response and advice!

I'm off to work now; I will follow the commands you suggested and post my success/failure later, for any others to observe.

Mike

---

### Post by mikodo on 2010-02-20
> **plucky said:**
> You have two entries for Medibuntu.One is in your /etc/apt/sources.list.
The other one is probably in /etc/apt/sources.list.d/medibuntu.list.

Use

```
gksudo gedit /etc/apt/sources.list
```

and put a **#** in front of this line ```
deb http://packages.medibuntu.org/ karmic free non-free
```

Then from a terminal ```
sudo apt-get update
``` and see if you still get the same error.

Good Luck

Thank you plucky. I ran the commands you suggested. I do not get the errors now. Here is an opportunity for me to learn about the # uncommenting lines and working with gedit. I just finished working two 12 hours shifts in the last two days and am very tired. I will explore this more at another time. 

Please see the screenshots below indicating the success we have achieved. I suppose I can now remove the medibuntu source in Software Sources that is now not checked; in case I forget and put a check in it later.

Mike

---

### Post by plucky on 2010-02-20
> **mikodo said:**
> Thank you plucky. I ran the commands you suggested. I do not get the errors now. Here is an opportunity for me to learn about the # uncommenting lines and working with gedit. I just finished working two 12 hours shifts in the last two days and am very tired. I will explore this more at another time. 

Please see the screenshots below indicating the success we have achieved. I suppose I can now remove the medibuntu source in Software Sources that is now not checked; in case I forget and put a check in it later.

Mike


Yes you can now remove that line.

Good Luck

---

