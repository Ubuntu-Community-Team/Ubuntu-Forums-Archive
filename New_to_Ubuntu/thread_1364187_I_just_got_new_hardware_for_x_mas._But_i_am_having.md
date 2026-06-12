---
title: "I just got new hardware for x mas. But i am having troubles."
date: 2009-12-25
forum: New to Ubuntu
---

### Post by utfan2012 on 2009-12-25
I just received 1TB HD and 1 GB ram for X mas, When i got done installing the hardware I tried to boot and it gave me this message,
One or more of the mounts listed in /etc/fstab/ cannot yet be mounted
/: waiting for dev/disk/by-uuid/e2cc783c-0516-48fa-ac19-da8fc48dd5d2
/tmp: waiting for (null)
swap: waiting for /dev/sdb1
/media/sdb3: waiting for /dev/sdb3

I wait, and I wait,and i am still waiting. But it will not boot.
Thanks For the Help.

---

### Post by taurus on 2009-12-25
How did you connect your new harddrive?  Make sure the hard that has Ubuntu on is the first device and the new harddrive as a second device.

---

### Post by utfan2012 on 2009-12-25
> **taurus said:**
> How did you connect your new harddrive?  Make sure the hard that has Ubuntu on is the first device and the new harddrive as a second device.

How do i do that?

I installed the New 1 TB hard drive it didn't have an option for master or slave, as far as i know, so i just plugged everything in and tried booting it.

---

### Post by taurus on 2009-12-25
Sounds like you have SATA drives.  The way you plug your harddrives to the mobo determine which one is first and which one is second.  Look into the BIOS to see which one is which.  Otherwise, reverse the cable from the harddrives to mobo.

Just off my head, the first harddrive should go into SATA0 on the mobo.

---

### Post by waspbr on 2009-12-25
yep, reversing the cables should do it, you could also look up the number of the SATA slots on your mobo manual.

---

### Post by utfan2012 on 2009-12-25
Wow i feel stupid, Thanks.

---

