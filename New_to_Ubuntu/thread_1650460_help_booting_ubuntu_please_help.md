---
title: "help booting ubuntu? please help"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by tyler0911 on 2010-12-21
I downloaded Ubuntu 10.4 recently (meaning today) using Wubi.  The installation seemed to go fine.  It took about an hour to load the preliminary files on my Windows Vista and then when it was done, I restarted my computer and booted into Ubuntu for the first time.  The setup went fine there, and then my computer turned off.  When I tried to boot into Ubuntu another time, it went to a DOS-ish screen, said some stuff I can't remember, and then acted like it was booting into Vista again.  After all of this was done, it went into the VAIO Disk Recovery interface (I'm on a Sony VAIO).  My Windows OS works fine now, except the time is off by 5 hours.  Help booting Ubuntu at this point?

---

### Post by bcbc on 2010-12-21
A fresh install of 10.04(.1) plus running the available updates (through Update Manager) will run a grub-pc update that breaks the install. See this [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Problem #2, Solution #1).

Since you've just installed, it's far simpler to uninstall, and reinstall Wubi. Then do not update packages grub-pc and grub-common (they're well down the list of updates under the "Recommended" updates section). That thread I provided also gives information on how to prevent these updates from appearing in the future.

---

