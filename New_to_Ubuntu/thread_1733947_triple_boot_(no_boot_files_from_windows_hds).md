---
title: "triple boot (no boot files from windows hds)"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Zakarum on 2011-04-19
Hi there. 

Let's see. I got a pc where I had : 

- One HD with W7
- One hd with xp

Somehow, and I don´t remember why it had a 3rd HD with only and all the boot files. This HD crashed so for now I can´t boot'em (still didn´t try to fixmbr and boot)

Now, I want to install an ubuntu in a New disk so I will try to do a triple boot (got it on my own pc and I'm happy with it :p ). I know I will have problems since into the 7 and xp hds have not any boot file inside. 

So... installing ubuntu, should I take anything into consideration before I **** it up even more?

I would install ubuntu and let the grub  try to detect the other 2 disk instalations, but I highly doubt it can since there's no boot files. Should I try to repair the boot from the windows's first? Is there any fast way to repair/create this boot files from the grub installation?

I know this is not a windows forum, but I hope you can help me out :p

Thanks in advance.

---

### Post by mynameisnotbob on 2011-04-19
Of course we can help.
Just partition it from liveCD boot. Put all the Windows files in the other partition, and proceed from there to fix your boot files (or just stick with Ubuntu).

---

### Post by oldfred on 2011-04-19
Grub only boots working windows. MBR systems boot from the MBR. Windows MBR jumps to windows partition PBR and loads the boot loader ntldr(XP) or bootmgr(Vista/7). Grub just bypasses MBR and jumps to windows PBR. If partition boot sector or boot files are not correct then windows will not boot.

You have to restore the boot files to each windows. Windows consolidates boots into the first one as it can only boot one partition, then either boot.ini or BCD control where the other installs are.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Do you have XP install disk to repair XP and the win7 repair CD to fix win7?

How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by mynameisnotbob on 2011-04-20
Ummm...what he said. :)

---

