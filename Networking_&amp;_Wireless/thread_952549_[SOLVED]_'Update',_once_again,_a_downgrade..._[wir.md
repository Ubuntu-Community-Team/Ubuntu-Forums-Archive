---
title: "[SOLVED] 'Update', once again, a downgrade... [wireless]"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2008-10-19
Access point not associated.

Update has un-configured my wireless. HPdv9428. 

Anybody got a link to point to? Checklist? Anything?

Thanks...

---

### Post by andrew.clegg on 2008-10-19
Try booting into the previous kernel version from GRUB -- just had to do this to get my girlfriend's wireless working again after last update. About to post about it...

Andrew.

---

### Post by buccaneere on 2008-10-19
> **andrew.clegg said:**
> Try booting into the previous kernel version from GRUB -- just had to do this to get my girlfriend's wireless working again after last update. About to post about it...

Andrew.

I'm sure that would work; how do I do that?

(I DID just post about it in 'install + upgrades' thread section!!!)

---

### Post by andrew.clegg on 2008-10-19
Instructions here:

[http://ubuntuforums.org/showthread.php?t=952569](http://ubuntuforums.org/showthread.php?t=952569)

The number of forums is a bit confusing isn't it -- didn't know whether to post mine in Dell or Laptops or Wireless or Upgrades or... :)

---

### Post by andrew.clegg on 2008-10-19
PS Your problem may not be exactly the same as ours, so no guarantees, obviously...

PPS I should have mentioned, if you just want to try booting the previous kernel to see if it does fix it, you can do this without editing anything. Reboot the machine and after the hardware test you should get a little 3-2-1 countdown before the Ubuntu splash screen comes up. Press ESC during this countdown and you get the GRUB menu, which will let you boot into the previous version of the kernel (2.6.24-19).

---

