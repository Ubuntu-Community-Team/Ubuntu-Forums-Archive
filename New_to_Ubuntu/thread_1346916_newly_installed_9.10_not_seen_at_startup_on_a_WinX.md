---
title: "newly installed 9.10 not seen at startup on a WinXP+8.04 machine"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Physicist on 2009-12-05
I had Windows XP on dev/sda, and 8.10 on dev/sdb on my computer. I then installed 9.10 on a new partition on sdb. I remember choosing to install grub file in sdb. Afterward, when I restart, I only see WinXP and 8.10, not 9.10. How could I fix it ?

---

### Post by mikewhatever on 2009-12-05
You need to boot from sdb to load Ubuntu, so enter the BIOS setup and change the boot order.

---

### Post by Physicist on 2009-12-05
In the Boot Sequence option of my BIOS configuration, I only see

1. Onboard or USB CD-ROM Drive
2. Onboard SATA Hard Drive
   Onboard IDE Hard Drive (not present)
   ...
3. USB Device (not present)


There doesn't seem to be a way to boot from sdb instead of sda. How to configure this ? Also, I'd like to see 8.04, WinXP, and 9.10 all listed at booting time. 


> **mikewhatever said:**
> You need to boot from sdb to load Ubuntu, so enter the BIOS setup and change the boot order.

---

### Post by mikewhatever on 2009-12-05
There should be a way to configure the Windows bootloader to point to sdbY, but I don't know how. Alternatively, the same can be done with grub, but first it needs to sit in the MBR of the hdd you can boot from. Just a thought, but perhaps a bios upgrade could also help.

---

