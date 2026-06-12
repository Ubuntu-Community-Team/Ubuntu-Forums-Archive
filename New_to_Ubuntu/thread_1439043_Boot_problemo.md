---
title: "Boot problemo"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by itsvan on 2010-03-25
Hi, im trying to boot my UBUNTU, but for some reason it takes me to this file check screen of some sort, it gets up to 14% and an error screen comesup saying the following: MOUNT OF FILESYSTEM FAILED. A maintenance shell will now be started. CONTROL-D will terminate this shell and retry...........so i do as it says. press Ctrl-D and it starts the checking screen but it fails again and returns to the same screen..WHAT CAN I DO???????????:o

---

### Post by rbc on 2010-03-25
Keep in mind, I have never had this problem (knock on wood), so my proposal is personally untested. In doing some searching for you, it seems that running a manually filesystem check should fix your problem. Instead of hitting Ctrl + D, let it drop to shell, then type:
*fsck*

You should then get prompted to allow the OS to do some checks and fixes. Feel free, though. to wait on advice from others, or do some more searching.

---

### Post by itsvan on 2010-03-26
IT WORKED .....a million thanks:D

---

