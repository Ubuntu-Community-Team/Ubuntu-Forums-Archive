---
title: "upgrading to WIn7 w/a dual boot system, want to avoid grub/MBR issues"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-01-20
Hey y'all,

I have a dual boot desktop, with my primary hard drive running Karmic and my secondary running Windows XP.  When I installed Karmic, I swapped my hard drives to their current configuration; before, my XP drive was primary and the (then unused) other drive was the slave.

Would it be possible to remove my Karmic drive, make the XP drive the sole drive, put Win7 on it, put Karmic back in the primary slot, and upgrade grub to reflect the new OS?

Thanks,

Red

---

### Post by cariboo on 2010-01-21
You will probably end up having to reinstall grub2, as Windows needs it's bootloader to be on the first partition of the first hard drive.

Have a look at this [page]("https://wiki.ubuntu.com/Grub2"), scroll down to Recover Grub 2 via LiveCD.

---

### Post by meierfra. on 2010-01-21
> Would it be possible to remove my Karmic drive, make the XP drive the sole drive, put Win7 on it, put Karmic back in the primary slot, and upgrade grub to reflect the new OS?

That should work.  It sound like Grub is installed in the MBR of the Ubuntu drive, so if you remove that drive,  Win 7 won't be able to touch it.  And running "update-grub" should automatically detect Win 7.  (But if things go wrong, the link in cariboo907 post will show you how to restore Grub)

---

### Post by Mark Phelps on 2010-01-21
> **Redmage913 said:**
> ... Would it be possible to remove my Karmic drive, make the XP drive the sole drive, put Win7 on it, put Karmic back in the primary slot, and upgrade grub to reflect the new OS?

That's exactly what I did, and once I reconnected the Ubuntu drive, booted from it, and ran update-grub, it found the Win7 install just fine and added the lines to the GRUB2 config file.

---

### Post by Redmage913 on 2010-01-21
Excellent! I'll try it tonight or tomorrow or let you know how it went.

---

### Post by Redmage913 on 2010-01-22
Yep, it worked! Windows even kept the same (arbitrary) drive letters, so I won't have any program conflicts.

Thanks for your input! Marking *SOLVED* now.

--Red

---

