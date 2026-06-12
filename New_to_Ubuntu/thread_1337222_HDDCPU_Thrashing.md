---
title: "HDD/CPU Thrashing"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by fleamour on 2009-11-25
I boot into Xubuntu, the latest kernel, & even before logging on, the HDD activity light flashes off & on in quick succession.  Log in & it continues.  The only process I can see in System Monitor is "gvfs-gdu-volume-monitor".  Under resources tab CPU is being thrashed as well, spiking at 100% is not unusual.

Any ideas?

---

### Post by ukripper on 2009-11-25
can you run top command and see which process is running and taking most CPU.
```
top
```

---

### Post by fleamour on 2009-11-25
update-notifier & devkit-disks-da share the top spot with udevd coming third.

---

### Post by ukripper on 2009-11-25
Have you updated through update-manager few minutes ago? Because sometimes update-notifer takes time to update database for update manager even after the updates.

So give it about 10 mins if it still there then we'll try something.

and can you tell us what is the spec of your computer.

---

### Post by fleamour on 2009-11-25
update-apt-xapi is now taking top spot.  Manually running update comes up with this error:

"An error occurred, please run Package Manager from right-click menu or apt-get in terminal to see what is wrong.  The error message was 'Error:  Opening the cache (E:read still have 9236500 to read but none left, E:The package lists or status file could not be parsed or opened.)'This usually means that your installed packages have unmet dependencies."

Rebooting does nothing.

I have a hoover crisis to attend to first (it's spitting blue sparks!)  But will get back to you soon as possible.

---

### Post by ukripper on 2009-11-25
looks like you got some dodgy repo in sources.list.

Can you post your sources.list here by running below command:
```
gedit /etc/apt/sources.list
```

BTW, i bought a cheap hoover from argos and had to clean it every time. i miss my broken dyson

---

### Post by fleamour on 2009-11-25
Had to install gedit:

# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)]/ karmic main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

RE:  Hoover, it was an Electrolux, graded stock with one year guarantee, like new.  After taking it apart, invalidating guarantee, I concluded it is impossible for stones to get into motor by design.  So must be electrical fault.  Still a new one is £40 delivered, so no great loss, but still. :(

---

### Post by ukripper on 2009-11-25
can you run this in terminal and see if it still throws any error:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by fleamour on 2009-11-25
"0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Still doing the same thing.

---

### Post by fleamour on 2009-12-13
Did a fresh install of Xubuntu after trying Puppy Linux for a while.  Managed to back up all important files even with HDD/CPU thrashing.  All running fine now.

I wonder if

```
sudo apt-get install ubuntu-restricted-extras
```

instead off

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Could of broke my installation?

---

### Post by ukripper on 2009-12-14
> **fleamour said:**
> 
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

Could of broke my installation?

no it is exactly the same thing. All it is doing extra is updating any newly added repo with update command before installing restricted-extra package.

---

