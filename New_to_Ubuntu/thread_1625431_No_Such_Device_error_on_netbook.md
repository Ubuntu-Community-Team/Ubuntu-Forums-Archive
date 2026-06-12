---
title: "No Such Device error on netbook"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by minhaz4u on 2010-11-19
I installed both win 7 and Ubuntu 10 on my netbook via USB flash. When i rebooted I'm getting "no such partition. Grub rescue error " 
I used a USB flash drive to boot from ubuntu live or win 7 to fix the boot menu. i created the bootable USB flash drive using unebootin.  Now Im not able to boot from the same USB. It gives me "no such device error"

---

### Post by sikander3786 on 2010-11-19
How was Ubuntu installed? Via Wubi or dual boot?

Regarding "no such device" error, make sure your USB drive is selected as First Boot Device in Bios menu.

---

### Post by minhaz4u on 2010-11-19
I prepared a bootable USB flash drive of UBUNTU 10.10 using Unebootin. After than I installed Windows 7 and while rebooting it gave me this error.
Ofcourse! I did change the boot option to USB. Infact I tried to boot from every possible option but still I'm stuck with the "No such Device" or "No such partition" errors. 
I'm using a netbook by the way. so no CD drives are available. Is there a way to fix this problem from the grub rescue prompt itself?

---

### Post by sikander3786 on 2010-11-19
You've installed Windows 7 and it is not booting either?

You were running Ubuntu fine previously ? But after installation of Windows, you are getting the Grub Rescue> prompt?

Actually I am a bit confused about your setup. Please clear it.

And you'll need to boot into an Ubuntu Live USB to do some commands.

If the computer is set to boot from USB drive and the USB is prepared correctly, that should not give "no such device" error as Grub is not related to it in any way.

There are some alternate options to create Live USB drives.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by bcbc on 2010-11-19
> **minhaz4u said:**
> I prepared a bootable USB flash drive of UBUNTU 10.10 using Unebootin. After than I installed Windows 7 and while rebooting it gave me this error.
Ofcourse! I did change the boot option to USB. Infact I tried to boot from every possible option but still I'm stuck with the "No such Device" or "No such partition" errors. 
I'm using a netbook by the way. so no CD drives are available. Is there a way to fix this problem from the grub rescue prompt itself?
It is possible to boot from a grub rescue prompt (thanks to the guide by *drs305*):
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by minhaz4u on 2010-11-21
Thanks all for helping me out here. The problem was with my corrupted bootable USB flash. I reformatted it in windows using MS DOS commands and made a bootable Windows 7 CD. Using fixboot and fixmbr commands in WRE, I got the netbook to load Windows 7 directly. 
In order to use the Ubuntu OS, I only had to re-install grub bootloader. Voila! Now I have my system up and dual booting :guitar:

---

