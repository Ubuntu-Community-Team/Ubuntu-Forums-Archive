---
title: "Boot issue with 9.04 and Win7"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Six_Digits on 2010-01-26
Probably a simple fix but heres what happened:

I had Windows 7 and Vista dual booting. I wanted to replace the Vista partition with 9.04, so I moved any files I wanted over to Win7 and wiped the Vista partition. Only halfway through did I wonder what this would do to the bootloader. 

I restarted just to see and of course, no bootable OS found. :(

I went ahead and installed Ubuntu 9.04 in the now empty partition, hoping I could fix it from Ubuntu. I tried using a recovery disc I found online, and it claimed to have found and fixed errors with Win7's MBR. Upon a restart, GRUB loads and starts Ubuntu right away.

Can I:
Add Win7 to GRUB?
Remove GRUB and try the recovery disc again?

Thanks ahead guys :)

---

### Post by 73ckn797 on 2010-02-05
Have you tried ```
update-grub
``` from terminal?

You can likely find a solution by searching using [http://www.uboontu.com](http://www.uboontu.com).

Also look here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by semi_fiction on 2010-02-05
Yes the first thing to try would be running 'sudo update-grub'. If that does not work, take a look at #16 in the thread that 73ckn797 posted.

---

