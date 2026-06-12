---
title: "install g++ on ubuntu 8.10"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by zeytin on 2009-10-20
can someone tell me how to install g++ on ubuntu 8.10, please?

---

### Post by Niko Johnson on 2009-10-20
```
sudo apt-get install g++ 
```

---

### Post by Bachstelze on 2009-10-20
```
sudo apt-get install build-essential
```
It will also install a bunch of other stuff, but g++ is virtually useless without it anyway.

---

### Post by zeytin on 2009-10-20
thanx for really quick reply,
i already tried whatever I found from ubuntu forums and google.

what am i suppose to do for the following, since i have no cd?
 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 5 newly installed, 0 to remove and 124 not upgraded.
Need to get 3942kB/7672kB of archives.
After unpacking 31.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  linux-libc-dev libc6-dev
Install these packages without verification [y/N]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

---

