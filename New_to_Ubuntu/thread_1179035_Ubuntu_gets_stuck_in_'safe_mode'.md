---
title: "Ubuntu gets stuck in 'safe mode'"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by rdheijer on 2009-06-05
Not the right term, but the best I could think of since I am somewhat nOObish to Linux.
 
Anyway, when I install Ubuntu via Wubi, which finishes perfectly, I restart my system and I end up in that fail safe or safe mode of ubuntu. So no desktop or regular bash, but the rescue shell.
 
I can't think of anything else then a problem with my hardware. Maybe you have the same problem when you look at the specs:
[LIST]
[*]AMD 9950 Phenom X4
[*]XFX  Mainboard with nVidia 750a chipset
[*]nVidia GTX260, but onboard chipset (nVidia 8200) as primary, hybrid SLI enabled (PCIe)
[*]LG-Blu-ray drive
[*]Seagate 2x 500G Pipeline HD (RAID 0)
[*]SB XFi Platinum (PCIe)
[/LIST]As you can read, I have my drives configured in a RAID 0 for speed (and yes, it's goes like lightning). Somehow I get the feeling the RAID configuration is the problem, that Ubuntu can't handle it.
 
Anyone with the same problem?
 
Webmasters: Could be I overlooked a topic. I'm the worst when it comes to forums. :)

---

### Post by overdrank on 2009-06-05
Hi and welcome, I would suspect that is would be the graphics SLI mode causing the issues.
I have no experience with wubi to be much assistants :)
Moved to Absolute Beginner Talk

---

### Post by Alias1407 on 2009-06-05
Head back to winblows and run in cmd...

```
chkdsk
```

Run it twice just to be safe, then head back to ubuntu, should work, if it doesn't then instead don't use wubi, use the installer inside Ubuntu.

---

### Post by rdheijer on 2009-06-09
Have been really busy lately, but thanks for the tips.
 
Seeing that my windows boot normally and apparently does not need a chkdsk, the problem with Hybrid SLI seems most likely then.
 
Though I have to say that the detection of my sata devices is reeeaaalllllyyyy sssslllooowwww.... :(
 
Anyway, step by step. Maybe someone else may benefit.

---

### Post by rdheijer on 2009-06-10
Ok, got one step further. The bootup (finally) reported that the filesystem isn't recognized. I hope this hasn't got anything to do with Windows Vista 64, though I very much doubt that.
 
I disabled the Hybrid SLI, Windows boots up perfectly.
 
The more I think of it, the more I believe that this is related to the RAID0 (stripe set) configuration of my harddrives. Sounds plausible to me:

[LIST]
[*]First RAID set is visible at boot time (probably by 'hardware' emulation)
[*]Ubuntu tries to boot
[*]{edit}Host filesystem is recognized, but controller seems to not have been recognized{/edit}
[*]Ubuntu stops to boot
[/LIST]Does anyone know if the nVidia 750a chipset is fully supported and also its' RAID support?

---

