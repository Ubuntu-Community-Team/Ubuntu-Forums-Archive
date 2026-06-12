---
title: "Missing BOOTMGR?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-07-05
I have a new Dell computer that has Windows 7. I bough a new 500GB drive for it, so now I have ~1TB.I have reinstalled and formatted the drives multiple time (trying to install Linux distros). I want to have Windows 7, Ubuntu, and Backtrack 4. Right now I have Windows 7 and Ubuntu on the 1st drive and Backtrack 4 partitioned on the 2nd drive. I was in Windows and I rebooted and I get a message saying "No Module Found. Aborted. Press Any Key" Then after that it says "BOOTMGR is Missing. Press Ctrl+Alt+Del to Reboot." I tried reinstalling GRUB2 usuing an Ubuntu live CD. I got GRUB reinstalled and now I could access any of the partitions. So I went into Windows and rebooted later and the same message came up again. What do you think keeps happening? Does something keep overwriting GRUB? If Windows was overwriting it, wouldn't it rewrite the Windows MBR?

---

### Post by okplayer02 on 2010-07-05
well first you must use the windows cd to fixmbr first then go behind it and install the grub so it can pick up your linux and windows installations.

---

### Post by Mark Phelps on 2010-07-06
> **walkerchuckwalker said:**
> ...What do you think keeps happening? Does something keep overwriting GRUB? If Windows was overwriting it, wouldn't it rewrite the Windows MBR?

Yeah, except, BOOTMGR is not the MBR, it is the boot loader for Vista/Win7.  So, it looks like your boot loader is getting clobbered.

---

### Post by okplayer02 on 2010-07-06
what is inside the MBR i thought it be the bootloader? i dont use windows so much you know better than I. Ill stick with Arch Linux ;)

---

