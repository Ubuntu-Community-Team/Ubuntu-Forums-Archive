---
title: "Help with Sources list"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2008-12-23
Hello all, I recently install the newest version of ubuntu via the live disc installer, and it royally ****ed my computer, so I installed an older version, Feisty to be precise, via the text installer. Now I'm trying to install xubuntu, however I continuously get this error message after typing any of either of these.

```

sudo apt-get install xubuntu-desktop
sudo apt-get install xfce-desktop

```

What I get is this from my terminal.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xubuntu-desktop

```

I have a feeling its got to do with my souces. The contents of my sources list is...

```

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

All help would be appreciated.

---

### Post by taurus on 2008-12-23
The repos for feisty are no good.  Therefore, you won't be able to install Xfce4 over the net.  Have you tried something a little newer like Hardy since you said that Intrepid didn't work for you?

---

### Post by Duck2006 on 2008-12-23
Feisty is out of date, this why your getting this error, you may want to try 8.04.

---

### Post by joshmuffin on 2008-12-23
Because Feisty is so out of date you wont be able to install Xfce.

I suggest you install Hardy LTS and then install it from there. Also make sure that you have the correct repo's enabled System > Administration > Software Sources.

My other suggestion is we could help you fix intrepid.

And if not those maybe a re-install or getting an xubutnu live cd (whatever version suits you).

Hope that was helpful, Joshmuffin

---

### Post by Narcoleptic_Insomniac on 2008-12-23
I don't have an install disc for 8.04

---

### Post by Narcoleptic_Insomniac on 2008-12-23
I'm going to try installing Kubuntu 8.10 and see how that turns out. Thanks for all your help.

---

### Post by Duck2006 on 2008-12-23
You can get one here.

[http://www.ubuntulinux.org/getubuntu/download](http://www.ubuntulinux.org/getubuntu/download)

---

