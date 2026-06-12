---
title: "uninstalling grub"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by adobrakic on 2009-04-22
I need to uninstall grub. I made a mistake by uninstalling Linux before uninstalling grub, because now I'm forced to do this from live-cd. This scratches out any methods that need to use CDs (super grub disc, for example), and I do not have a Windows recovery CD. 

I've looked at the ms-sys method, but I wasn't sure how to do it and I didn't want to mess anything up. I know that I can also put super grub on a flash drive, but I'm not sure how to do that either.

Any help?

---

### Post by adobrakic on 2009-04-23
okay, well i fixed this issue, but now i have another grub-related issue.

I installed ubuntu wubi not too long ago, and uninstalled it, but for some reason the wubi grub is still there. can i get rid of this?

---

### Post by adobrakic on 2009-04-25
bump

---

### Post by zeex on 2009-04-25
> **adobrakic said:**
> okay, well i fixed this issue, but now i have another grub-related issue.

I installed ubuntu wubi not too long ago, and uninstalled it, but for some reason the wubi grub is still there. can i get rid of this?

Can you post the content of file boot.ini ?

How to open boot.ini?
Start -> Run -> {type}C:\boot.ini 

Let's see what it says then we can figure out why grub is still there :)

---

### Post by adobrakic on 2009-04-25
C:\boot.ini doesn't exist, and I searched in C:\ for 'boot.ini,' and no results came up. :x

---

### Post by Elfy on 2009-04-25
what ms is it - vista uses something else I think - other than that I'll not be of much help :(

---

### Post by zeex on 2009-04-25
> **adobrakic said:**
> C:\boot.ini doesn't exist, and I searched in C:\ for 'boot.ini,' and no results came up. :x

I guess you are using Vista. well let me know your OS. IF you are using vista, you need to download a small application called [EasyBCD]("http://neosmart.net/dl.php?id=1"). You can read about EasyBCD in [wiki]("http://en.wikipedia.org/wiki/EasyBCD"). It is used for configuring windows vista bootloader. [check this link]("http://neosmart.net/wiki/display/EBCD/Configuring+the+Bootloader") out for configuring EasyBCD. Open ***_configure boot_*** and look for line **_Ubuntu/Wubi_**. Delete this line and save the settings. 

I am assuming you 've already removed ubuntu and wubi. Do this only after removing ubuntu and wubi.

Good luck :)

---

### Post by adobrakic on 2009-04-27
Sorry for the late replay, but yes, I have Vista.
I've edited (I think) my boot with EasyBCD, but haven't tried it yet. 

I'll find out on next reboot.

Thanks!

---

### Post by Alterax on 2009-04-27
If you purchased your computer with Vista and it didn't come with the install discs, you should have the option of making your own Vista DVDs.  

Check in the programs that were preinstalled by your OEM; if you've decided to stick with Vista instead of switching, it would be prudent to make a set before you actually need them.  You can also use them to reinstall Vista's default bootloader.

---

### Post by Herman on 2009-04-27
Neosmart thoughtfully provides a free    [Windows Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") for fixing your Windows Vista or Windows7 boot loader with. It's a free download and it's not large, it should only take a few minutes.
It seems like an Installation CD but it only has the repair tools in it and no installation files. You can't use it for installing or re-installing Windows.
You can use it to run 'Startup Repair', which can fix a few Windows booting problems automatically.
 'Startup Repair' can't re-install BCD to MBR for you, but all you need to do is go to a command prompt and run BOOTREC  /FIXMBR for that.
Other commands include BOOTREC /FIXBOOT, BOOTREC /REBUILDBCD and  CHKDSK, and more.

---

