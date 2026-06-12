---
title: "Update Manager error 407 (proxy) but no Proxy here!"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by DampCat on 2010-06-12
Hey guys.

My 9.10 update manager is failing with the error message:

Failed to fetch blah.blah.package.name 407 Proxy Authentication Required

However, I have no Proxy settings in use on this laptop. The only proxy settings i use are set in Firefox using foxyproxy and are currently turned off. I've been to the Network Proxy settings and set Direct internet "system wide" but this hasnt helped.

It's preventing me from installing the last few updates and also from upgrading to 10.04.

I read somewhere that it might be that the source list is messed up or something, but I have no idea how to change it or what to. I've googled the error and all instances are from people who are behind a proxy, which im not

Anyone got any clues? 
I'll follow this post with the things i've tried so far if it helps to rule out any options.

---

### Post by DampCat on 2010-06-12
Sudo apt-get update
[quote=terminal]
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/karmic/free/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/karmic/non-free/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
[/quote]

Sudo apt-get upgrade
[quote=terminal]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/quote]

Additionally, i tried changing the server Ubuntu uses from Main to UK and back again, it does nothing to help. Using the option to "find best server" also result in a "there are no servers" dialogue.

Using sudo gedit /etc/apt/sources.list reports I'm using 9.04, but
[quote=terminal]
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
[/quote]

So not sure if that's something to worry about.

---

### Post by DampCat on 2010-06-13
More googling has revealed nothing, and the only references i can find on the Ubuntu boards to the 407 is from people who are behind firewalls or proxies, of which i'm using neither :(

Could really use some help with this, i'm completely at a loss!

---

