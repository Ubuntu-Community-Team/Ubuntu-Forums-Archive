---
title: "ndiswrapper - need &quot;make &quot; command"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Carmel on 2006-08-12
Hi there, I'm a relative newbie in linunx/ubuntu, so it would help if I could get a little more detailed information.

I'm trying to follow this thread [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588) to get my linksys adapter working. However, after downloading ndiswrapper, I need to use the make command to do the install process. The guide states that I should install the build-essentials pack, but I am unable to do so as the computer with linux has no internet access on it. Could someone please advise? Thanks.

---

### Post by aysiu on 2006-08-12
The *build-essential* package is on both the Desktop CD and Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by NetworkGuy on 2006-08-12
NDISWrapper 1.8 is available via Synaptic.

It was good enough to bring my WPC54G v2 on-line.

---

### Post by az on 2006-08-13
You rarely need to recompile ndiswrapper.  Use the version provided.  Use the very latest .inf file for your device (the one that shipped in the box may be too old).

ndiswrapper-utils is in the same place as build-essential, on any Ubuntu CD.

---

