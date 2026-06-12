---
title: "Kernal Panic error - after 9.10 Update Mgr update"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by SYBU on 2009-11-13
Newbie to Ubuntu/Linux. I recently upgraded from 9.04, which was working fine on dual boot PC Compaq Presario - XP, to 9.10.  Last night Update Mgr performed some security updates. This morning I restarted the 9.10 and it froze during the boot process. Here are the boot screen results:
 
[ Linux-bzImage, setup=0x3400, size=0x3b26e0]
[ Initrd, addr=0x37864000, size=0x78b4f5]
[ 0.963213] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2) 
"FROZE"
 
 
I also tried the recovery mode boot option and it freezes as well. I can boot into XP fine.
 
Again, I'm new to Linux and would welcome some help with my next steps to resolve this issue. thanks.
SYBU

---

### Post by lrcaballero on 2009-11-13
Try a clean installation, make sure to back-up all your data first!!! Linux is very friendly with other OS's, the install will walk you through the partition is very simple!!

If it doesn't work after a clean install, well then I recommend that you go back to 9.04 and wait for a couple of months until you try again, the Karmic is fairly new and there is still some issues been reported by the community, that I am sure the developers are working as we speak!! Follow the threads and comments on Karmic and see for your-self.

Good Luck

(If is not broken (9.04) don't fix it!!)

Luis

---

### Post by SYBU on 2009-11-13
Thanks for your advise. However, I'm not sure I understand what you mean by "clean installation" I originally installed 9.04 and 9.10 via WUBI in XP.
 
Currently, I can't get into 9.10 to perform any commands backup or otherwise. So do you mean backup by Windows data? Please provide more detail.
 
Thanks.
 
SYBU

---

### Post by lrcaballero on 2009-11-13
I thought you were dual booting!!! my mistake SORRY!! you are using wubie correct? well in this case delete the file in wubie and start the installation again. I have never use wubie but I am assuming is just like VMWare, Virtual PC, etc. So yeah delete Ubuntu from wubie and do a new Ubuntu 9.10 Karmic Koala installation again from a Live CD and/or ISO image which-ever applies to you.

Luis

---

### Post by SYBU on 2009-11-13
Maybe it was my mistake. When I power on my Compaq during the boot process I'm presented with a menu and can choose to boot XP or Ubuntu. I'm calling that Dual boot.   I'll will try another 9.10 installation.
 
Thanks again for your advise.

---

### Post by lrcaballero on 2009-11-13
Good Luck!!!!

---

