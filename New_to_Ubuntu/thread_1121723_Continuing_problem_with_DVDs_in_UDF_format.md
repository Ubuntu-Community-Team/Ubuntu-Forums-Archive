---
title: "Continuing problem with DVDs in UDF format"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by hatrack on 2009-04-10
Hi all !

A couple of days ago, I posted to this forum on this matter (See "Problems reading DVDs").

Since then, I have done more searching and have found what appears to be possible solutions to install the necessary compatibility features into Hardy. Unfortunately, these do not work. I guess that this is because Hardy is continually evolving with new up-dates, bug fixes, etc. Searching under Synaptic, I have found the package libudf0 and reason that this should sort the problem. Unfortunately again, although this installs apparently correctly, the system still reports "Unable to mount UDF volume" when presented with a DVD made under Vista.

I have only been running Ubuntu for about 6 months, although I have considerable experience of MS software stretching back 25 years. In the old days of DOS (before Windows) a feature such as UDF compatibility had to be "activated" by an entry in config.sys. I am wondering whether such a file is used by Ubuntu and if so, where abouts is within the file system and ... is this truly the solution to my problem ?

The Ubuntu documentation seems very chaotic to me and that on the Canonical site no help at all. Can anyone please suggest/recommend technical books on the workings of Linux/Ubuntu which are of about the same technical level as the old books that used to be produced for DOS ?

Many thanks and best regards to all ...

---

### Post by LowSky on 2009-04-10
Stop using the Built in Vista DVD recorder, and the problem will go away. Simple as that.

The problem is Vista supports the newest version of suppprt (2.60), whilemany OSes including the Linux Kernel supports only up to 2.50. Even Windows XP cant read some UDF created from Vista.
[http://en.wikipedia.org/wiki/Universal_Disk_Format#Native_OS_support](http://en.wikipedia.org/wiki/Universal_Disk_Format#Native_OS_support)

---

