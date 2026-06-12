---
title: "Jaunty crash and now won't boot up"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by titania177 on 2009-05-28
I have a Dell XPS M1330 laptop, I upgraded to Jaunty a few weeks ago, everything was fine until the last few hours. It kept freezing, I would have no choice to switch it off by holding down the power button. And now it won't boot up again, even if I select the recovery boot in the menu (am not very technical, sorry!). Now it says 

"Target filesystem doesn't have /sbin/init. No init found. Try passing init=bootarg"

I don't know what to do! What does this mean? I don't have a way of booting from a Live CD right now... is there anything else I can do?

Thank you.

---

### Post by Hospadar on 2009-05-28
Sounds like maybe a hard drive problem.  Either something bad happened to the partition or maybe the disk is dying (or maybe something else completely)

I'd boot up off a livecd, and open up gparted (Alt-F2, type, without quotes, "gksu gparted").  From here you can view all your partitions, you should see the ext3 or 4 partition you installed ubuntu to.  If you right click on the partitions, you can check them and see if you get any errors.

---

