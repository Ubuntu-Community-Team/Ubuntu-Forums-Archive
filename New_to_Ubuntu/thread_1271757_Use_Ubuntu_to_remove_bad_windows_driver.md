---
title: "Use Ubuntu to remove bad windows driver?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by jacobi on 2009-09-21
Hey all

I <3 Ubuntu but I still have to use windows xp sometimes. I decided to try out driverMax to update my windows drivers to the latest versions. It said I had a newer driver available for my USB devices so I went ahead and downloaded it.  Now I can not use my usb devices on windows.

If I had a PS2 keyboard or mouse, I could just roll back the driver, alas I do not.

This brings me to here to ask this question: Can I use Ubuntu to manually navigate to the windows folders on the system and get rid of the new naughty driver? Or should I just stop by the local Goodwill and find me a PS2 mouse?

Thanks all

Jacobi

PS Dual booted with Winxp/Ubuntu

---

### Post by LowSky on 2009-09-21
if you know the driver name and how to auto mount the windows partition fomr ubuntu than yes you can, but windows might just reinstall that driver when you boot back into it.

---

### Post by 3rdalbum on 2009-09-21
If you can find where the bad driver is installed, then yes you could possibly remove it. Not knowing anything about Windows, the main problem with the plan is that the new driver might have overwritten the old driver, so erasing the new driver would not cause your USB to work again.

Borrow a PS2 mouse or keyboard.

---

### Post by LowSky on 2009-09-21
> **3rdalbum said:**
> If you can find where the bad driver is installed, then yes you could possibly remove it. Not knowing anything about Windows, the main problem with the plan is that the new driver might have overwritten the old driver, so erasing the new driver would not cause your USB to work again.

Borrow a PS2 mouse or keyboard.

Windows XP will just try to  download the driver from the  microsoft repos...? (do they call them that...lol)

---

### Post by mikechant on 2009-09-21
Windows should be able to come up with at least basic generic USB mouse/kb drivers if you delete the bad driver. Recent Ubuntu versions should have ntfs-3g (stable NTFS read/write support) preinstalled.

If not you could try the Windows repair option if you've got the disc. But this might risk your Ubuntu install if it screws up.

---

