---
title: "NVIDIA drivers not installing"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Rayve on 2010-02-05
On my newly built comp with a fresh install of 9.10 64-bit, I've been having trouble getting the NVIDIA drivers to install.  I've tried going to System > Administration > Hardware Drivers, and I select the 185 as that's the recommended one, but it gets to Downloading and then fails with "installArchives() failed" error and closes out.

I've also tried downloading the 190.53 directly from NVIDIA's site, but that fails because it says I'm still in X, even though I did a "killall x" and ended up logging myself out of Gnome, so I re-logged in with an xterm session but still got the same error about running an x-server.  How do I close it down?

I've also tried following this guide: [http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers) but I'm stuck on the module-assistant part.  When I do the m-a auto-install line, it tells me I maybe don't have contrib or non-free in my sources list and it ignores the file.  Here is my source list:

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted contrib non-free

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted contrib non-free

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe contrib non-free
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe contrib non-free

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse contrib non-free
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse contrib non-free
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse contrib non-free

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

# added 05 Feb for nvidia issues
deb http://http.us.debian.org/debian stable main contrib non-free
deb http://non-us.debian.org/debian-non-US stable/non-US main contrib non-free
deb http://security.debian.org stable/updates main contrib non-free 

```Also, I have two NVIDIA 250 cards in SLI.  Any thoughts?

---

### Post by Cabs21 on 2010-02-05
just a thought.  Dont know what card you are using since you built machine yourself.  You are positive that your Nvidia card is a 64-bit chipset.  That is the first thing that pops into my head when you said 64-bit install.  Also is the 64-bit install necessary for your machine?

---

### Post by ratcheer on 2010-02-05
Detailed instructions are on page 1 of this thread:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Rayve on 2010-02-05
ratcheer,

Thanks, I think that did it!

It took a bit of quick typing, because every few seconds an error message of sorts would come up and interrupt my command once I entered the "sudo /etc/init.d/gdm stop" line.  It looked like this:
```

4:1:2: usb_set_interface_failed

```
with ever-increasing numbers before it, sort of like [49850.125] or something.  Is this something I should fix / be worried about?

Thanks!

---

