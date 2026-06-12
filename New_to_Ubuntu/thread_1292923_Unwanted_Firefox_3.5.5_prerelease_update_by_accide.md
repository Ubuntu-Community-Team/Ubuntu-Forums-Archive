---
title: "Unwanted Firefox 3.5.5 prerelease update by accident"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by peachtree195 on 2009-10-16
I am running 64-bit ubuntu Jaunty 9.04. 
I was recently trying to update my standard Firefox3.0 to Firefox 3.5. I was following a few of commandlines from the internet some of them were not working fully, some of them the computer sput out as errors on the way. As it was happening i was trying other solutions found on the way to end up clicking some Synaptics Package manager checkboxes. 

I ended up with my Firefox 3.5.5 prerelease. I would like to find out how to come back to a regular 3.5 non-pre-release version and, more importantly how did it happen that what I installed a prerelease version.

---

### Post by lavinog on 2009-10-16
is it possible you added a ppa for mozilla?

post the output of:
```

cat /etc/apt/sources.list /etc/apt/sources.list.d/*

```

---

### Post by LowSky on 2009-10-16
what instructions did you follow

Also Firefox 3.5 in 9.04 will show up are as Shiretoko, no matter what.

Its technically the final release of 3.5 but without the firefocx branding

---

### Post by peachtree195 on 2009-10-16
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu) jaunty main
# channel for the jaunty partner channel
# 
#:description:This channel contains the partner software for jaunty 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# channel for the jaunty partner channel
# 
#:description:This channel contains the partner software for jaunty 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

---

### Post by peachtree195 on 2009-10-16
The first thing I found on updating i followed such instructions:

1. Open your Terminal and run following command *echo ‘deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’ >> /etc/apt/sources.list*
 *echo ‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’ >> /etc/apt/sources.list*
  *sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 247510BE*
 3. Now run below command on your terminal
 *sudo apt-get update && sudo apt-get install firefox-3.5*

But then i run into trouble with the keys, so i got the update a couple of times, than it stopped asking for keys, then i discovered firefox is sitting in synaptics package manager and clicked a box there for FF 3.5.

Where am I right now i have no idea :)

---

### Post by lavinog on 2009-10-16
I don't see the mozilla ppa in your sources.list anymore.
try removing firefox-3.5 then update then reinstall it

```

sudo apt-get purge firefox-3.5
sudo apt-get update
sudo apt-get install firefox-3.5

```

---

### Post by Wolfhere on 2009-11-06
> **lavinog said:**
> I don't see the mozilla ppa in your sources.list anymore.
try removing firefox-3.5 then update then reinstall it

```

sudo apt-get purge firefox-3.5
sudo apt-get update
sudo apt-get install firefox-3.5

```

Worked like a charm for me. I had Shiretoko. And because the branding was for Shiretoko, my Zimbra administration did not work. Does now, thanks a lot.):P

---

### Post by Wolfhere on 2009-11-06
BTW, this procedure installed Firefox 3.5.4

---

