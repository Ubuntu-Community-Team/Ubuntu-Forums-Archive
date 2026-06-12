---
title: "Wrath of the Lich King DvD Locked!"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by Unisaga on 2009-08-29
So I inserted my DvD. And i can see the installer, but I can't access it! I have no idea why. I can't change the permissions and accessing it with nautilus just Error's, and Wine doesn't even want to load. I have no idea what to do. Anyone got an idea?

---

### Post by rajeev1204 on 2009-08-29
> **Unisaga said:**
> So I inserted my DvD. And i can see the installer, but I can't access it! I have no idea why. I can't change the permissions and accessing it with nautilus just Error's, and Wine doesn't even want to load. I have no idea what to do. Anyone got an idea?


Please ask in sub forum gaming and leisure.You will find a lot of threads already posted on wow.

What do you mean by 'i cant access it'?

---

### Post by Drakebyte on 2009-10-04
If you see only 'DirectX' and 'Install.exe' in the DVD's directory, then please try this:

> sudo mount -o remount,unhide /dev/cdrom
gksudo nautilus /media/cdrom0

Depending on your system, cdrom0 and cdrom may need to be replaced with the specific of your system. You should then be able to install from the DVD with Wine, it works for me at least.

Good luck!

**This is on 9.10, but I have no reason to believe this won't work with 9.04**

---

