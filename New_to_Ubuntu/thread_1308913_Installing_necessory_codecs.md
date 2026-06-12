---
title: "Installing necessory codecs"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by notstevek on 2009-11-01
I'm trying to install mp3 codecs for rhythm box but, I saw that you had to install gstreamer (then again, this wasn't for karmic), and mediubuntu repository which I did but I got errors..

So yeah, lol, anyone care to help :)

---

### Post by kansasnoob on 2009-11-01
What errors?

Run this command:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

Then for 32 bit (i386):

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

Or for 64 bit:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 w64codecs
```

If you encounter any errors copy and paste them here.

---

### Post by notstevek on 2009-11-01
Here you go:
> steve@steve-ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
>  --output-document=/etc/apt/sources.list.d/medibuntu.list &&
> sudo apt-get -q update &&
> sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
> sudo apt-get -q update
[sudo] password for steve: 
--2009-11-01 01:22:52--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2009-11-01 01:22:52 (21.3 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [65.9kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
  404  Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
  404  Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources
  404  Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
  404  Not Found



> steve@steve-ubuntu:~$ sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate

---

### Post by wilee-nilee on 2009-11-01
You might try switching servers go to software sources then choose other then I think it's best server for it to probe for the fastest ping. Also tick on all the repositories in software sourcse.

---

### Post by Prince.Paul.K on 2009-11-01
Try manually installing it through synaptic.

Synaptic> Origin > packages.medibuntu.org/nonfree >

Then install non-free-codecs and w64codecs.

---

### Post by notstevek on 2009-11-01
@ wilee
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.Yeah.. I'm on Ubuntu atm, so..

@ prince,

> non-free-codecs:
 Depends: ubuntu-restricted-extras  but it is not installable or
     kubuntu-restricted-extras  but it is not installable or
     xubuntu-restricted-extras  but it is not installable


---

### Post by kansasnoob on 2009-11-01
Go to System > Administration > Software Sources and click on the Other Software tab. Make sure the Partner repo is checked.

Then try this again:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by notstevek on 2009-11-01
@kansas,
all are checked, still gives me:
> steve@steve-ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate

---

### Post by kansasnoob on 2009-11-01
Post the output from terminal of:

```
cat /etc/apt/sources.list
```

---

### Post by notstevek on 2009-11-01
here you go:
> steve@steve-ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic multiverse
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security main restricted
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security main restricted
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security universe
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security universe
deb [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security multiverse
deb-src [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) karmic main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

---

### Post by kansasnoob on 2009-11-01
Well that looks fine.

Go back to Software Sources and try changing "download from" to the Main Server or some other server.

---

### Post by notstevek on 2009-11-01
> **kansasnoob said:**
> Well that looks fine.

Go back to Software Sources and try changing "download from" to the Main Server or some other server.

comes out with:
> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by kansasnoob on 2009-11-01
Well, color me puzzled! The only thing I'd know is that the servers are totally swamped.

You could possibly download the individual .debs but it would be sloppy and slow:

[http://packages.ubuntu.com/karmic/ubuntu-restricted-extras](http://packages.ubuntu.com/karmic/ubuntu-restricted-extras)

Could actually cause some real borkage!

---

### Post by notstevek on 2009-11-01
> **kansasnoob said:**
> Well, color me puzzled! The only thing I'd know is that the servers are totally swamped.

You could possibly download the individual .debs but it would be sloppy and slow:

[http://packages.ubuntu.com/karmic/ubuntu-restricted-extras](http://packages.ubuntu.com/karmic/ubuntu-restricted-extras)

Could actually cause some real borkage!

Installing any debs do not work as well, because I tried installing the flash player deb and first it gave me an error, that I forgot, and can't seem to get back, and gives me a network error now each time, and if I try it via software center, it gives me 'not available for your hardware architecture'

I'm not a new user to Ubuntu, I've been off and on since fiesty. But this just confused me to no other..

I'm either assuming I should have went with the x64 since I do have phenom quad core, but I've never had a problem using 32bit, that and my wireless card, but I don't see how the internet works then..

---

### Post by wilee-nilee on 2009-11-01
I'm not sure if the medibuntu and restricted need the backports open but I always open those up, if you look at the apt/source list you posted they are blocked.

---

### Post by notstevek on 2009-11-02
> **wilee-nilee said:**
> I'm not sure if the medibuntu and restricted need the backports open but I always open those up, if you look at the apt/source list you posted they are blocked.

Sorry for the late reply guys, opened those up, ran sudo apt-get update, still no luck :(

---

