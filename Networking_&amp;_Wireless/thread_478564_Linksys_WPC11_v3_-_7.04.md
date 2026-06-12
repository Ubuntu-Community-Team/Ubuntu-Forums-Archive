---
title: "Linksys WPC11 v3 - 7.04"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by cremate on 2007-06-19
Hello!

Supposedly this card will work out of the box according to the Wiki. But I have not been able to get it working yet and I assume that is because the wiki is outdated with that card (08/2005).

Does anyone have any ideas how to get this thing working with 7.04?

If I boot up with the card it, it locks up during the network setup, and I have to hard reboot.  If I insert the card during runtime, it has locked up once, but I blacklisted some RALink drivers (I dont think it even uses them) and it didnt lock up next time.  It even connected to my router but I got a strange ip address and no internet activity (I could ping localhost though).

Anyway, please let me know if anyone knows of a fix for this.  Perhaps ndiswrapper, but I have little experience with that.

---

### Post by cremate on 2007-06-19
OK!  I found someone with the same exact problem!

The advice here solves the problem.

[http://ubuntuforums.org/showthread.php?t=442558&highlight=wpc11](http://ubuntuforums.org/showthread.php?t=442558&highlight=wpc11)

Thanks!

---

