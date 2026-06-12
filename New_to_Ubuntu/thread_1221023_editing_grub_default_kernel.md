---
title: "editing grub default kernel"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by shadow120 on 2009-07-23
i updated to karmic for testing and the default kernel dosent support some of my drivers but the other kernel that is in the grub menu at start up works how do i set the other kernel to default   thanks

---

### Post by drs305 on 2009-07-23
If you are using grub legacy you can install startupmanager and set it via a gui application. The link on how to do this is in my signature line under "SUM". Startupmanager has lots of ways to safely tweak the grub menu.lst  The link also includes info on how to manually edit the file.

If you want to do it manually, open menu.lst and look for the "default 0" line and change it to the correct number. The first title in the bottom section is 0, the second 1, etc. The safest way is just to add or subtract from whatever is currently booting. So if default is 0, and you want it to boot the title two entries lower than what it is currently booting, change it to "default 2"
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst

```

If you aren't sure, you can post your menu.lst

---

### Post by shadow120 on 2009-07-23
that worked thanks alot

---

