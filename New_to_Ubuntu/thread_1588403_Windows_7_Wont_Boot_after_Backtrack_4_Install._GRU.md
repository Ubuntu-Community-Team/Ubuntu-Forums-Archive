---
title: "Windows 7 Wont Boot after Backtrack 4 Install. GRUB problem."
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Longcort on 2010-10-04
I installed backtrack 4 R1 on a seperate hard drive than my windows 7 install. For some reason it installed grub on the windows hard drive too but it wont load windows. It gives me an error.

I believe my MBR is borked, is there a way to re-apply the windows MBR. But the problem is that I dont have the Windows 7 x64 Ulti CD I need to repair it.

Is there any way I can reapply the Windows MBR on the Hard-drive without a CD?

---

### Post by sandyd on 2010-10-04
> **Longcort said:**
> I installed backtrack 4 R1 on a seperate hard drive than my windows 7 install. For some reason it installed grub on the windows hard drive too but it wont load windows. It gives me an error.

I believe my MBR is borked, is there a way to re-apply the windows MBR. But the problem is that I dont have the Windows 7 x64 Ulti CD I need to repair it.

Is there any way I can reapply the Windows MBR on the Hard-drive without a CD?

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

next time, please remember to create your windows 7 recovery discs.

or, if you feel like being a techie person... run
```

bootrec /FixMbr 

```
in the recovery cd command prompt

---

### Post by oldfred on 2010-10-05
If you have the windows CD the above will work.

If you want a basic boot loader you can do this. The windows boot loader in the MBR does not do much. It looks for the active partition  (boot flag) and jumps to that partition to continue booting. Lilo does the same but expects to find more lilo code. Ignore those errors on install of lilo to the MBR.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

