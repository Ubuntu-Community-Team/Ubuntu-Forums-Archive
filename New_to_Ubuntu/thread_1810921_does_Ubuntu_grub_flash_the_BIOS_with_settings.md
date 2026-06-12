---
title: "does Ubuntu grub flash the BIOS with settings?"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by s1baker on 2011-07-23
hi,
I was wondering if the Ubuntu grub makes any flash setting to the BIOS?

Here is what happened to me:
I have 2 hard drives (EIDE) connected in my box on one ribbon. Both are Ubuntu HD's, and they both boot just fine, I can select in the BIOS which one to run as the main OS drive, and the other I can copy to.
 I also have a Windows XP HD in my box that I connect every now and then to play one game, and that's the only reason that I have the XP HD. Yesterday after I connected the XP HD ( of course, I always completely power off and unplug every thing, then connect the XP HD to the ribbon, and reverse when I go back and hook up the Ubuntu HD's ), the BIOS would not recognize the Ubuntu HD's. I tried switching the ribbons, pulling the pin tabs and trying different configurations, nothing would work, not even the exact same way that the Ubuntu HD's were set originally. Finally I reset the BIOS to the default setting that it has, and every thing worked.

Question:
 Does the Ubuntu grub flash the BIOS with some type of setting ( that the Windows XP boot erased? or could perhaps Windows itself have flashed some settings to the BIOS that fouled up my Ubuntu HD's?

Thanks
( I am using Ubuntu 10.10 32 bit )

---

### Post by wildmanne39 on 2011-07-23
Hi, I am not sure what is causing your problem but no the grub does not flash your bios.

---

### Post by amjjawad on 2011-07-24
> **s1baker said:**
> hi,
I was wondering if the Ubuntu grub makes any flash setting to the BIOS?

Here is what happened to me:
I have 2 hard drives (EIDE) connected in my box on one ribbon. Both are Ubuntu HD's, and they both boot just fine, I can select in the BIOS which one to run as the main OS drive, and the other I can copy to.
 I also have a Windows XP HD in my box that I connect every now and then to play one game, and that's the only reason that I have the XP HD. Yesterday after I connected the XP HD ( of course, I always completely power off and unplug every thing, then connect the XP HD to the ribbon, and reverse when I go back and hook up the Ubuntu HD's ), the BIOS would not recognize the Ubuntu HD's. I tried switching the ribbons, pulling the pin tabs and trying different configurations, nothing would work, not even the exact same way that the Ubuntu HD's were set originally. Finally I reset the BIOS to the default setting that it has, and every thing worked.

Question:
 Does the Ubuntu grub flash the BIOS with some type of setting ( that the Windows XP boot erased? or could perhaps Windows itself have flashed some settings to the BIOS that fouled up my Ubuntu HD's?

Thanks
( I am using Ubuntu 10.10 32 bit )

GRUB has absolutely NOTHING with that. Your problem obviously with BIOS. Why? simply because when you reset to the default settings, it worked.

GRUB's Job comes after BIOS's job, not before if you know what I mean :)

---

