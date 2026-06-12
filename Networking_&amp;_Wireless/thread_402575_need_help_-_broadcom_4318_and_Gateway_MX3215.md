---
title: "need help - broadcom 4318 and Gateway MX3215"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by gcos7 on 2007-04-05
I downloaded Ubuntu linux 6.10 desktop a several months ago and had it dual booting with XP and had the wireless working via ndiswrapper.

I had to get rid of my linux partitions temporarily for a large windows project, and now have reinstalled ubuntu 6.10.  Now I can't get my wireless to work.  I have tried downloading more than 1 version of ndiswrapper, but they all return errors when I do the make's.  Checked according to install file for the libraries in lib but nothing is found, which I assume is why it is not working.

I remember that previously all I did was download ndiswrapper and the drivers I needed and then ran ndiswrapper to load the drivers after rmmod'ing the old.  It did not have all of the make's, etc., that are in the current distros of ndiswrapper.

I am NO EXPERT at linux, so any help would be greatly appreciated.  I have followed instructions posted on other sources and still cannot get the new ones to work.

Thanks!
Dave Eaton

---

### Post by spd106 on 2007-04-06
If you are attempting to build ndiswrapper you will need to install the build-essential package and the kernel headers for your current kernel version. This should be fairly simple to accomplish through Synaptic, though you will need an Internet connection.

---

