---
title: "Install deb package for VLC in Ubuntu 8.10"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by vincent chin on 2009-01-18
I have downloaded a  libdvdcss2_1.2.9-1_i386.deb for VLC to play real media properly.However, it can't process with error:

```

sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb
dpkg: error processing libdvdcss2_1.2.9-1_i386.deb (--install):
package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 libdvdcss2_1.2.9-1_i386.deb

```

I am using Intel processor.It should be compatible with i386 package without any mismatch issue.
Thank you.

---

### Post by stderr on 2009-01-18
It looks like you grabbed a 32-bit package and you're running a 64-bit system?

Anyway, libdvdcss2 is available in Medibuntu repos. You shouldn't be installing that via a .deb. It won't get automatically updated!

See [this]("http://ubuntuforums.org/showthread.php?t=766683") post, follow the first instructions under Part 1 - Essential Packages, then scroll down to Part 4 - DVD Playback and follow the instructions. You don't need to follow the bit about changing to Xine - just the first bit.

I've paraphrased what you need to do here too (ripped from the above guide) & assuming you're running Intrepid Ibex (8.10):

1) Add the Medibuntu repo to your application sources:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

2) Add the Medibuntu public key so you don't get warnings, and update the package cache:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

3) Install the DVD menu packages:

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4
```

---

### Post by gjoellee on 2009-01-18
You can install VLC using a simple command:
```
sudo apt-get install vlc
```

---

### Post by arjuntank on 2009-01-18
> **gjoellee said:**
> you can install vlc using a simple command:
```
sudo apt-get install vlc
```

apt-get rocks!

---

### Post by oldos2er on 2009-01-18
You need the 64-bit libdvdcss: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)

---

### Post by igknighted on 2009-01-18
libdvdcss is for playing encrypted DVDs, not real media.  But the above posts will let you install it properly.

---

### Post by kansasnoob on 2009-01-18
> **oldos2er said:**
> You need the 64-bit libdvdcss: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)

I'm thinking along the same lines. If the OP wants to be sure whether they're running 64 bit or not they could run in terminal:

```
uname -m
```

64 bit would show x86_64, 32 bit would show i686

---

### Post by vincent chin on 2009-01-18
> **stderr said:**
> It looks like you grabbed a 32-bit package and you're running a 64-bit system?

Anyway, libdvdcss2 is available in Medibuntu repos. You shouldn't be installing that via a .deb. It won't get automatically updated!

See [this]("http://ubuntuforums.org/showthread.php?t=766683") post, follow the first instructions under Part 1 - Essential Packages, then scroll down to Part 4 - DVD Playback and follow the instructions. You don't need to follow the bit about changing to Xine - just the first bit.

I've paraphrased what you need to do here too (ripped from the above guide) & assuming you're running Intrepid Ibex (8.10):

1) Add the Medibuntu repo to your application sources:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

2) Add the Medibuntu public key so you don't get warnings, and update the package cache:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

3) Install the DVD menu packages:

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4
```

Thank for your post.It seem like a big 'misleading' on the name of libdvdcss2_1.2.9-1_i386.deb.I just need to install codecs for real media not for dvd plaback.How should I configure it?Sory for confusing as I am absolute new to Ubuntu.

I am running on intel 32 bits system,really weird that .deb detect it as amd64:confused:

---

### Post by vincent chin on 2009-01-18
> **gjoellee said:**
> You can install VLC using a simple command:
```
sudo apt-get install vlc
```

It had been installed.However no video screen displayed when real media is played,it just let me to listen it.:confused:

---

### Post by stderr on 2009-01-18
You just need to enable medibuntu repo and install restricted codecs. [This guide]("http://ubuntuforums.org/showthread.php?t=766683") should help

---

### Post by vincent chin on 2009-01-19
Well, I already enable medibuntu repo and install restricted codecs.But rmvb media still not display properly in neither one of the player.I have tried on smplayer,vlc,mplayer,totem.Attach with content of the file sources.list



```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe
#deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid maino6

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu intrepid universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse universe


```

---

### Post by oldos2er on 2009-01-19
For real media you might need to install Realplayer; maybe someone else can confirm or deny that vlc can "handle" real media.

 If I were you I'd uncomment the partner repository.

---

