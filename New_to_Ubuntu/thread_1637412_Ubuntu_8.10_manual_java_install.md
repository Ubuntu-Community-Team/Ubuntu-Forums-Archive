---
title: "Ubuntu 8.10 manual java install?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Drumm3r4lyfe on 2010-12-04
I went away from the linux scene for awhile only to find when I came back that Ubuntu 8.10 is no longer supported.

I have been able to install a java plugin for web applets in the past in 8.10, however there are sources missing now, I think.

The way I used to install java was:

System-Administration-Software Sources and I checked the first 4 boxes and unchecked the rest. I would reload sources and then sudo apt-get update and finally sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin, however that doesn't work anymore.

This is what I get now for apt-get update.
```
ubuntu@ubuntu:~$ sudo apt-get update
Ign http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security Release
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid Release 
Ign http://security.ubuntu.com intrepid-security/main Packages
Ign http://archive.ubuntu.com intrepid-updates Release
Ign http://security.ubuntu.com intrepid-security/restricted Packages
Ign http://security.ubuntu.com intrepid-security/multiverse Packages
Ign http://security.ubuntu.com intrepid-security/universe Packages
Ign http://archive.ubuntu.com intrepid/main Packages
Ign http://archive.ubuntu.com intrepid/restricted Packages
Ign http://archive.ubuntu.com intrepid/multiverse Packages
Ign http://archive.ubuntu.com intrepid/universe Packages
Err http://security.ubuntu.com intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.37 80]
Ign http://archive.ubuntu.com intrepid-updates/main Packages
Ign http://archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://archive.ubuntu.com intrepid-updates/universe Packages
Err http://security.ubuntu.com intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://security.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
Err http://archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.169 80]

```

As a result of this...

```
ubuntu@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

```

And my sources.list:

```
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb http://archive.ubuntu.com/ubuntu intrepid main restricted multiverse universe

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu intrepid-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu intrepid universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid universe
# deb http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb-src http://archive.ubuntu.com/ubuntu intrepid-updates universe
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu intrepid multiverse
# deb-src http://archive.ubuntu.com/ubuntu intrepid multiverse
# deb http://archive.ubuntu.com/ubuntu intrepid-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu intrepid-updates multiverse
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

Now on first thought I tried burning a 10.04 cd as that is the newest LTS, however when trying to boot I see the purple ubuntu screen with dots loading, then the screen goes black and only a terminal like screen is left.

Is there anyway to still manually install a java plugin on 8.10 using a livecd, or am I forced to upgrade somehow?

Also, I'm still a beginner with linux, so try to keep the terms simple ;)

Thanks!

---

### Post by yeats on 2010-12-04
> I went away from the linux scene for awhile only to find when I came back that Ubuntu 8.10 is no longer supported.

Yes for some reason, the 8.10 section of archive.ubuntu.com is no longer there.

> Is there anyway to still manually install a java plugin on 8.10 using a livecd, or am I forced to upgrade somehow?

You'll need to upgrade, but don't look at it negatively.  10.04 adds many features that were not present in 8.10.

> Now on first thought I tried burning a 10.04 cd as that is the newest LTS, however when trying to boot I see the purple ubuntu screen with dots loading, then the screen goes black and only a terminal like screen is left.

Sounds like a problem with the X server and your video card.  I would recommending downloading the alternate cd version of 10.04:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

If you're having problems with the display after upgrading, start a new thread with that issue.

---

