---
title: "Can't install or build ImageMagick"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-26
I installed ImageMagick just fine on my computer using Synaptic. Tried installing it on the wife's computer, and Synaptic tells me:

```

imagemagick:
 Depends: libmagickcore2 but it is not going to be installed
 Depends: libmagickwand2 but it is not going to be installed

```

So I go to the imagemagick website and download the source, and build. When the configure stage is finished, I check the summary it says that that JPEG support (among many other things) is not enabled.

The JPEG library IS present, in /usr/lib/libjpeg.so.62 (which appears to be soft-linked to libjpeg.so.62.0.0 in the same directory.)

Please help, I'm at my wits' end here!

---

### Post by snova on 2009-03-26
What version are you using?

Also, what are the contents of the /etc/apt/sources.list file?

---

### Post by Volt9000 on 2009-03-26
The version I have installed on my computer is 6.3.7 8/21/08 Q16 according to the output of convert -version. According to Synaptic it's 7:6.3.7.9.dfsg1-2ub.

The version I'm trying to compile on the other computer is 6.5.0.9, the latest from the ImageMagick website.
Synaptic lists the latest version as 6.5.0.0-2.
Interesting how in my Synaptic there's a different version of ImageMagick...

Anyways here is the sources.list file:

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb ftp://ftp.debian.org/debian experimental main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://packages.medibuntu.org/ free non-free
deb http://jbrout.free.fr/download/debian binary/

```

---

### Post by Volt9000 on 2009-03-26
Ok, so I backed up the sources.list file and copied over my own from my computer. That listed the older version of ImageMagick and I *COULD* install that.

But this feels like cheating; I really wanted to fix the problem "properly". And this begs the question: how come the newer version of ImageMagick can't install but the older version can?

---

### Post by snova on 2009-03-26
> **Volt9000 said:**
> The version I have installed on my computer is 6.3.7 8/21/08 Q16 according to the output of convert -version. According to Synaptic it's 7:6.3.7.9.dfsg1-2ub.

I was wondering the Ubuntu version you were running, actually, but that's helpful anyway. :) It says under your avatar that you are running Intrepid, but the ImageMagick package does not depend on the libraries in the first post in the first place... but it does in Jaunty.

> ```

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
**deb ftp://ftp.debian.org/debian experimental main**
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://packages.medibuntu.org/ free non-free
deb http://jbrout.free.fr/download/debian binary/

```

Most of that file looks pretty normal, but that line has me concerned. I don't think you can add Debian repos to Ubuntu without breaking things.

Post the output of this, please:

```
apt-cache policy imagemagick
```

---

### Post by Volt9000 on 2009-03-26
Both computers are running Intrepid.

So I uninstalled ImageMagick and reverted to the previous sources.list file so we can figure this out.
Here's the output of apt-cache policy imagemagick:

```

imagemagick:
  Installed: (none)
  Candidate: 7:6.5.0.0-2
  Version table:
     7:6.5.0.0-2 0
        500 ftp://ftp.debian.org experimental/main Packages
     7:6.3.7.9.dfsg1-2ubuntu3 0
        500 http://archive.ubuntu.com intrepid/main Packages

```

Ok, I understand now... since that experimental repository was present, and had a copy of a newer version of ImageMagick, Synaptic displayed only the newer version and hid the older one.

So I went into Synaptic and disabled that distro, and now I see the same version as the one on THIS computer! Installed it, worked like a charm!
Fantastic, thank you so much! :D :D :D

---

