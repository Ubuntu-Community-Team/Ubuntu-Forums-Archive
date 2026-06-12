---
title: "Driver Question, How do i find out what hardware I have!?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2010-01-15
Hi,
I'm just after completing a fresh dual boot with xp and ubuntu...
Ubuntu is working fine, but I do not have any drivers for xp (graphics etc is not correct).

Is there any easy way to find what hardware my computer has? 

Perhaps could anyone tell me is there a terminal command that might list my hardware!? ...

This is so i can search for drivers. Its a custom built computer which was not originally mine and not a standard model. Must I open up the computer and read the info off the various parts! In device manager in windows the video drivers are not listed.. would a driver detective programmes work for these basic drivers!

---

### Post by warfacegod on 2010-01-15
Open a terminal and type:

```
sudo lshw
```

---

### Post by marshmallow1304 on 2010-01-15
Also see [sysinfo]("apt://sysinfo"), which gives you a nice GUI with categories.

---

### Post by dearingj on 2010-01-15
I prefer [hardinfo]("apt:hardinfo") for identifying my computer's hardware

---

