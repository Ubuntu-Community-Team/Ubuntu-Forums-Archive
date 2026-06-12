---
title: "Reset repository sources list?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-10-22
Hi,

I seem to have messed up my list of repositories and was wondering if there was a way to reset it to the default, or if there was an example file anywhere showing the default settings.

When I try to install packages the speed of download is really slow (on lots of connections).

I tried to change from main server to my local UK one, but each time I do it reports:

> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


I've tried a couple of UK based ones, each time producing the same result.

Thanks for any help, it's appreciated :)


EDIT - This is my current file:

> 
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty multiverse
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security main restricted
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security main restricted
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security universe
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security universe
deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security multiverse
deb-src [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) jaunty-security multiverse


---

### Post by Elfy on 2009-10-22
You could use this to regenerate a new source list.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by philinux on 2009-10-22
Here's mine from jaunty. 
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
```

In a terminal try this and report back any errors.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by revanb on 2009-10-22
It may not be your sources file:

1) Could be a temporary network issue that will pass.
2) Make sure your own network settings are correct.


Lastly, always do the following before changing any settings files:

```
sudo cp settingsfile settingsfile.backup.date
```

replace as necessary.

---

### Post by jtodaro on 2009-10-22
> **forestpixie said:**
> You could use this to regenerate a new source list.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

How stable is the use of this to regenerate the sources.list? The reason I ask is I went ahead and backed my current list up, regenerated a new one (I am running 9.10 karmic and confirmed before I swapped sources.list files that nothing was currently outstanding). When I ran an update after swapping file it showed a tremendous amount of updates outstanding.

---

### Post by Elfy on 2009-10-22
If you are running karmic why does you sources.list in post #1 appear to be jaunty?

There are no karmic updates today - the repos are frozen I believe.

If you currently have jaunty packages then setting the source list to karmic would result in a long list of supposed updates

---

### Post by jtodaro on 2009-10-22
> **forestpixie said:**
> If you are running karmic why does you sources.list in post #1 appear to be jaunty?

There are no karmic updates today - the repos are frozen I believe.

If you currently have jaunty packages then setting the source list to karmic would result in a long list of supposed updates

Different person as I didn't make post #1.

---

### Post by Elfy on 2009-10-22
> **jtodaro said:**
> Different person as I didn't make post #1.

heh - well did you add exactly the same things to the new one as you had in the old one - for instance did you add ppa's you didn;t have before?

Hard to tell without comparing - if you edited the file with gedit there should be a backup.

I've used the tool to create sources lists in the past.

What I will say is that currently there are no updates to karmic assuming that you had previosly updated.

---

### Post by jtodaro on 2009-10-22
> **forestpixie said:**
> heh - well did you add exactly the same things to the new one as you had in the old one - for instance did you add ppa's you didn;t have before?

Hard to tell without comparing - if you edited the file with gedit there should be a backup.

I've used the tool to create sources lists in the past.

What I will say is that currently there are no updates to karmic assuming that you had previosly updated.

Can't guarantee that I added exactly the same stuff as before and to be honest, I probably added more to the updated one as I got checkbox happy :) It just has me questioning my past two upgrades from the original 8.x CD install I came from.

---

### Post by Elfy on 2009-10-22
Well if you didn't replace like for like that would explain that.

I was updated yesterday in Karmic and have had no updates since then, I just checked.

You say you have a backup, check them or remove the extras then do an update and see if there is anything new then.

---

### Post by jtodaro on 2009-10-22
> **forestpixie said:**
> Well if you didn't replace like for like that would explain that.

I was updated yesterday in Karmic and have had no updates since then, I just checked.

You say you have a backup, check them or remove the extras then do an update and see if there is anything new then.

While I agree it's best to compare like to like, in regard to updates via aptitude, it shouldn't install anything that wasn't previously there as all dependencies should be met at install time (or so I would think). Unless somehow one of the additional repositories I added somehow had an updated version of a current package I have installed (and also newer version than even the main repos I have already in my sources.list). Either way, I streamlined it and now it comes back clean. Very odd occurrence.

---

