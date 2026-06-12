---
title: "[SOLVED] GRUB installed to second HDD."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by OldDogNewTricks on 2008-12-29
I just did a new install of Ubuntu 8.10 to a PC with two HDDs.  I wanted to keep Windows XP on the main drive, and install Ubuntu 8.10 on the second drive.  It seemed to work fine, but there now appears to be a big gotcha in the install.

When I take out the second HDD for any reason, it appears that GRUB was installed on it, instead of on HDD 0 (my WinXP drive).  This renders WinXP inaccessible. (No GRUB on HDD 0, no boot possible.)

I would have thought GRUB would be installed on HDD 0, so it was on the same drive as the MBR.  It wasn't.  So I went back, and reinstalled Ubuntu, looking for a place where I could tell the installation where to put GRUB.  I never found that option!

So how do I put GRUB on HDD 0 and Ubuntu on HDD1 ?

---

### Post by jimmy the saint on 2008-12-29
This issue seems to crop up a lot lately.
Here is a thread that seems to have some good solutions
[http://ubuntuforums.org/showthread.php?t=1018493&highlight=grub+external](http://ubuntuforums.org/showthread.php?t=1018493&highlight=grub+external)

---

