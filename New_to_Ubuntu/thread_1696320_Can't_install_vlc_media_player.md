---
title: "Can't install vlc media player"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by nazmy on 2011-02-27
I've tried to install the vlc media player on ubuntu 10.10 using command line. But, the system gave me this:

nazmy@nazmy-HP-G42-Notebook-PC:~$ sudo apt-get install vlc
[sudo] password for nazmy: 
Sorry, try again.
[sudo] password for nazmy: 
Sorry, try again.
[sudo] password for nazmy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
       Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
                libavcodec-extra-52 (>= 4:0.6-1~) but it is not installable
       Depends: libavutil50 (>= 4:0.6-1~) but it is not installable or
                libavutil-extra-50 (>= 4:0.6-1~) but it is not installable
       Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
       Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not installable
       Depends: libtar but it is not installable
       Depends: libva-x11-1 but it is not installable
       Depends: libva1 but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Depends: libxcb-randr0 (>= 1.1) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not installable
       Recommends: vlc-plugin-notify (= 1.1.4-1ubuntu1.4) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.4-1ubuntu1.4) but it is not going to be installed
E: Broken packages
nazmy@nazmy-HP-G42-Notebook-PC:~$ 

Please help me, thanks :-)

---

### Post by Perfect Storm on 2011-02-27
It might be that some or all of the sources in your sources.list are disable.

Please open the terminal, and post the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by sites on 2011-02-27
Did you enable the "backport" and "partner" repos in your sources list?

---

### Post by oldos2er on 2011-02-27
Try ```
sudo apt-get install -f
sudo apt-get update
```

---

### Post by nazmy on 2011-02-28
> **Artificial Intelligence said:**
> It might be that some or all of the sources in your sources.list are disable.

Please open the terminal, and post the output of this:
```
cat /etc/apt/sources.list
```

nazmy@nazmy-HP-G42-Notebook-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
nazmy@nazmy-HP-G42-Notebook-PC:~$

---

### Post by vivek.pandey on 2011-02-28
why arent you trying to install it from software center.. ? try from there and see you get any error message or not

---

### Post by nazmy on 2011-02-28
> **neo_aryan said:**
> why arent you trying to install it from software center.. ? try from there and see you get any error message or not

I've tried using the software center.. this is what came out:

Package dependencies cannot be resolved

---

### Post by vivek.pandey on 2011-02-28
n did you try synaptic ?

---

### Post by nazmy on 2011-02-28
> **neo_aryan said:**
> n did you try synaptic ?

Yes, I did

---

### Post by vivek.pandey on 2011-02-28
what error did you get there?

---

### Post by nazmy on 2011-02-28
> **neo_aryan said:**
> what error did you get there?

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libavcodec52 (>=4:0.6-1~) but it is not installable or
     libavcodec-extra-52 (>=4:0.6-1~) but it is not installable
 Depends: libavutil50 (>=4:0.6-1~) but it is not installable or
     libavutil-extra-50 (>=4:0.6-1~) but it is not installable
 Depends: libqtcore4 (>=4:4.7.0~beta1) but it is not installable
 Depends: libqtgui4 (>=4:4.5.3) but it is not installable
 Depends: libsdl-image1.2 (>=1.2.10) but it is not installable
 Depends: libtar  but it is not installable
 Depends: libva-x11-1  but it is not installable
 Depends: libva1  but it is not installable
 Depends: libxcb-keysyms1 (>=0.3.6) but it is not installable
 Depends: libxcb-randr0 (>=1.1) but it is not installable
 Depends: libxcb-xv0 (>=1.2) but it is not installable
 Recommends: vlc-plugin-notify but it is not going to be installed
 Recommends: vlc-plugin-pulse but it is not going to be installed

---

### Post by vivek.pandey on 2011-02-28
i guess you need to repaar your vlc package try this thread

[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

---

### Post by nazmy on 2011-02-28
Problem solved, thanks anyone :-)

---

