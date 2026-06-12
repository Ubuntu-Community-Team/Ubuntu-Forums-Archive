---
title: "can't boot after failed install"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by craigh158 on 2009-05-01
Just tried to install the latest Ubuntu from CD on a dual boot system with Windows 2000.  Each system has its own HDD.  The install failed and appears to have messed up grub.  I now can't boot the computer into Windows or at all.  Ubuntu was not installed so the only access to my computer is by booting off the CD.  I need access to Windows as well.

I tried to edit grub, but that failed.  Any suggestions to fix this?

---

### Post by billgoldberg on 2009-05-01
Try out this live cd:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

That should boot up Windows just fine.

I believe you can fix this using the Windows cd as well, not sure.

---

### Post by Bigjge on 2009-05-01
I have had this problem before.   Windows just insert set-up disk and when get to repair
type FIX BOOT should solve problem, if not go to install and then will find installed os and will say new or repair. repair.  Have had to do this and always works.

---

### Post by NightwishFan on 2009-05-01
You can use super grub disk to fix Windows MBR. It is called "fix boot of windows" on the CD I believe. I have tested this.

---

### Post by Niniel on 2009-05-01
How did the installation fail?
Did you get any error messages?

---

### Post by craigh158 on 2009-05-01
I was in a bit of a hurry so I didn't record the message (thought I could duplicated it later).  It said something about CD speed and to try to burn at a slower speed.

Problem is now solved though.  I was doing the original install from Windows.  I tried it again after booting Ubuntu from the CD and clicking on the Install icon.  This time it worked and I now have a dual boot system.

Thanks.

---

