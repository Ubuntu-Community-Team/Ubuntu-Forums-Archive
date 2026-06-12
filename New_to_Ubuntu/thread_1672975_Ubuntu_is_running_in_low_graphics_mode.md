---
title: "Ubuntu is running in low graphics mode"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by pszkraba on 2011-01-21
I'm new to Linux and installed Mint 9 in a dual boot configuration with Windows XP on my Toshiba M50 with 1 gig of ram and an Intel GMA 900.

Everything seems to work fine until I close the cover then open up the lid (from suspend). Usually, within about 5 minutes or so, I get "Ubuntu is running in low graphics mode". When I let it go into low graphics mode, I don't see any difference in the graphics quality.  The only change I see is when I check my monitor status under the control center.  It will tell me that it can't detect the monitor. Normally, it will detect laptop monitor.

Can anyone help me with this problem?  I'd really like to dump Windows entirely, but find this error very annoying as it causes me to lose all my work.

Thanks

---

### Post by NightwishFan on 2011-01-21
I would say the short term solution is not to suspend for now. Set it up so it only blanks the screen when you close the lid under Power Management in the gnome control area.

This does not mean that this will always happen to the machine, perhaps someone can help you debug suspend bugs more and in future versions of the kernel such things might not happen. I would like to ask, does the machine shut down when this occurs? Is that what you meant by lose your work?

If it does not shut down after the suspend bug open a terminal and run this command:
```
dmesg > dmesg_log
```

There should then be a file called dmesg_log in your home folder. Right click it and choose compress, and compress it as a .gz file. Upload that gz file here as an attachment. That way we can review the system log.

---

### Post by pszkraba on 2011-01-21
> **NightwishFan said:**
> I would say the short term solution is not to suspend for now. Set it up so it only blanks the screen when you close the lid under Power Management in the gnome control area.

This does not mean that this will always happen to the machine, perhaps someone can help you debug suspend bugs more and in future versions of the kernel such things might not happen. I would like to ask, does the machine shut down when this occurs? Is that what you meant by lose your work?

If it does not shut down after the suspend bug open a terminal and run this command:
```
dmesg > dmesg_log
```

There should then be a file called dmesg_log in your home folder. Right click it and choose compress, and compress it as a .gz file. Upload that gz file here as an attachment. That way we can review the system log.
I have to use "Run Ubuntu in low-graphics mode for just one session" which reboots it and I lose anything I'vr been working on.

---

### Post by NightwishFan on 2011-01-21
This makes me suspicious it is perhaps a Nvidia driver issue, if you have Nvidia. From what I hear they do not play nice with suspending.

---

### Post by pszkraba on 2011-01-22
> **NightwishFan said:**
> This makes me suspicious it is perhaps a Nvidia driver issue, if you have Nvidia. From what I hear they do not play nice with suspending.
I have an Intel GMA 900

---

