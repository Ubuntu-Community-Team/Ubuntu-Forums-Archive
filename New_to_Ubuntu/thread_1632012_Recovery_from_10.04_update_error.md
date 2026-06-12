---
title: "Recovery from 10.04 update error"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by ter0880 on 2010-11-27
Hi, I have an Averatec 6220 Notebook with an inoperable cd/dvd (so boot option is HD only, no usb flash). I successfully installed 10.04 using Wubi for dual boot with WinXP; everything worked -- wifi, lan, music, firefox, open office apps. All was well until I used update manager and it froze about 90% into installation of updates. 
 
On reboot it detected partial update installation error, made corrections and some progress, but froze again. On further reboot it now hans up at "Ubuntu 10.04" screen with error message: "The disk drive for / is not ready yet or not present" with these options: wait (no good), press S to skip (no good) or M manual recovery, which when selected, ends with "root filesystem check failed" and a cursor prompt in maintenance shell.
 
Is there a command to "undo" the updates or otherwise fix this installation? I'm committed to make this work, but I've already reinstalled once and I'd like to avoid a third if possible.
 
Thanks in advance, new Ubuntu user, 
 
ter0880

---

### Post by cariboo on 2010-11-29
You would probasbly be better off trying to fix the error than to try and roll back an update. Start in recovery mode, and once at the menu select dpkg, it should download and install the rest of the packages needed to complete the update.

---

