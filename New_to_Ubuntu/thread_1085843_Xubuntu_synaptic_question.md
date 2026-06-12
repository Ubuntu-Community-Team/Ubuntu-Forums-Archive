---
title: "Xubuntu synaptic question"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by pocket_andy on 2009-03-03
Hi guys,
I have just installed xubuntu 8.10. I can't see some programs in synaptic such as Kile (or lyx), fityk, open office and Kbibtex. I think I must be missing some repositories. In repositories, I have all the options ticked. Any help would be much appreciated.
Thanks,
Andy

---

### Post by Michael.Godawski on 2009-03-03
hi,

can you please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by cwsnyder on 2009-03-03
Do you have any of the Third Party repositories enabled?

I checked on fityk and OpenOffice.org, and my Synaptic lists them, but I am not sure which repository it wout be.

I have Canonical's Intrepid Partner  repository listed on my 8.10 install along with the Medibuntu repository, Cairo Dock, and Virtual Box repositories, but have no idea which would have those programs.

---

### Post by pocket_andy on 2009-03-03
yep, I get:
> ~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


---

### Post by plucky on 2009-03-03
> **cwsnyder said:**
> Do you have any of the Third Party repositories enabled?

I checked on fityk and OpenOffice.org, and my Synaptic lists them, but I am not sure which repository it wout be.

I have Canonical's Intrepid Partner  repository listed on my 8.10 install along with the Medibuntu repository, Cairo Dock, and Virtual Box repositories, but have no idea which would have those programs.

Just right click on the program and go to **Properties** will tell you what repository it comes from.


@pocket_andy

From a terminal ```
sudo apt-get update
``` and then see what is listed in synaptic.


Good Luck

---

### Post by pocket_andy on 2009-04-17
Thanks for help!

---

