---
title: "ndiswrapper-utils-1.9 package not found"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by cmosguy on 2008-05-17
Hey all,

I'm attempting to install Ubuntu 8.04 (and any linux distro for that mattter) for the first time.  Last night, I was able to get my wireless card to work by using ndiswrapper (thanks to another thread in the forum!).

However, I've encounter a problem today, when I moved from the LiveCD to an installation within Windows (with wubi).  This time, when I type this command in the terminal window:

sudo apt-get install ndiswrapper-utils-1.9

I get an error message that the package ndiswrapper-utils-1.9 isn't found.  I've checked the typing several times now, so I'm pretty certain that I'm typing it exactly the same as the other day.  Any suggestions?

---

### Post by cmosguy on 2008-05-17
I figured it out.  The ndiswrapper has to be installed from the CD, which wasn't in the drive (it found it before, when I was using the LiveCD).  I ended up using the Package Manager, had to add the CD, then installed it from there.

Wireless working now...

---

