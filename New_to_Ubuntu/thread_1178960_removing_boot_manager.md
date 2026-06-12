---
title: "removing boot manager"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by DaSilver on 2009-06-05
Hi, I'm new to ubuntu and so I ran into so trouble. Here's the story: I have 3 OS (WinXP, Vista, Win7) on 3 partitions of 1 HDD, but then I descided to install an additional OS (Ubuntu). I failed to lauch the wuki.exe from XP and Vista (it just didn't do anything) so I thought maybe I can then just boot in after the reboot (like a regular instaltion), but instdead of using my HDD, I will use my memory stick (4gb). So I did, but now I have a bit of a problem. If I remove my memory stick, I cannot load into anything: it does not load the boot menu with my 3 OS like it used to, insdead it says that something needed for loading is missing (cannot clerify right now what excatly). Any suggestions how to remove this re-loading thing? (but If I insert the memory stick, I have 4 choices I think: Load ubuntu, Load ubuntu (savemode) Load Ubuntu (memorytest), Other versions of windows, and the last Load into Vista boot loader (this is were I get my old boot menu with the 3 OS).

---

### Post by DaSilver on 2009-06-05
The msg that it displays says: GRUB loading 1.5, error 21.

---

### Post by Alias1407 on 2009-06-05
Boot to a windows cd and choose the recovery mode and type...

```
C:\>  fixmbr
C:\>  fixboot
C:\>  bootcfg /rebuild
C:\>  exit
```

The bootcfg command will ask you for a load identifier. This is
the Windows boot menu entry and can be anything you want—
“Windows” is a good choice. When prompted for OS Load Options,
just leave the line blank and hit Enter.

---

### Post by DaSilver on 2009-06-05
Thank you! Dunno how, but it worked. I didn't input those commands, but simply inserted the WinXP install CD and (maybe) it did everything for me. :D
Thank you again!

---

