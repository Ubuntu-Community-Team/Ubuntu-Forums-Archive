---
title: "Update GRUB while in LiveCD session"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-09-07
I shut down the 'puter and the printer simultaneously. On reboot, GRUB hangs and all I see is the cursor, blinking, about 2 inches from top screen and in leftmost column.

I tried rebooting several times. I even removed the power cord and hit the on-off switch to insure a solid ground. No joy there.

How do I get the 'puter to run a GRUB update while in LiveCD session / mode?

---

### Post by Mark_in_Hollywood on 2011-09-07
This is resolved by looking into the BIOS. For some odd reason, the system was booting from a USB drive (flash or thumb drive) and there is no OS on that drive. Resetting the BIOS to look for the "boot" drive solved the problem.

---

### Post by nmanoogian on 2011-09-07
This has happened to me a few times before too. If you're like me and you always leave a flashdrive in, you can go into the BIOS and change the boot order. It should be in boot settings

---

