---
title: "Startup sets new"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by bpazolli on 2007-11-27
I am probably doing something wrong, but I have gotten my wireless to work but every time I restart it disappers from the device list and such. However once I type sudo modprobe ndiswrapper it all comes back to life. Is there something to stop it resetting or failing that an equivalent to the autoexec.bat in windows to run this line automatically at startup?

---

### Post by bpazolli on 2007-11-27
I'm solving all of my own problems today. I seem to have got it working by adding the line sudo modprobe ndiswrapper to /ect/init.d/rc.local

---

