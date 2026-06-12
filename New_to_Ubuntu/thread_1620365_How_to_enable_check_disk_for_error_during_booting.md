---
title: "How to enable check disk for error during booting"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by darshan123 on 2010-11-13
Hi,

I want to check my disks for errors during boot-up time. How do I enable it so that Ubuntu does it the next time I restart ?

Thanks,
-Darshan

---

### Post by darshan123 on 2010-11-13
got to know there is a count of reboots upon which ubuntu will trigger this automatic check. Where can I find that count ? (Probably i will set count to 1 and reboot).

---

### Post by ssulaco on 2010-11-13
> **darshan123 said:**
> Hi,

I want to check my disks for errors during boot-up time. How do I enable it so that Ubuntu does it the next time I restart ?

Thanks,
-Darshan
open up a terminal and run this command ```
sudo touch /forcefsck
``` you will be asked for your password,type in your password even though you wont see it displayed,...reboot the computer and the fsck will kick in.
note:this is a one time check...

---

### Post by ssulaco on 2010-11-13
> **darshan123 said:**
> got to know there is a count of reboots upon which ubuntu will trigger this automatic check. Where can I find that count ? (Probably i will set count to 1 and reboot).
30 boots,or when the system is interrupted (power outage)
you can change the boot count by this guide
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

