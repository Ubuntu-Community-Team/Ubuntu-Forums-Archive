---
title: "How to dual boot?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by winslowevan on 2011-06-10
I have the latest ubuntu and I tried installing windows xp without doing anything but putting in the disc and it would only boot windows and not fully install then I had to go through the trouble of deleting windows. Okay so the real question is [COLOR=Red]what preparations do I need to make a dual boot system so I can choose the system each time. Thanks.[/COLOR]

---

### Post by nzjethro on 2011-06-10
Boot Ubuntu from a live CD, then use Gparted to resize your Ubuntu partition, and create a partition for XP. Then insert the XP disk, and choose the partition you created in Gparted.
After you install XP you may have to reload Grub, as XP will replace Grub with the Windows MBR.
Before you do it, make sure you've backed up your system, in case things go pear shaped.

---

### Post by winslowevan on 2011-06-10
Thank you very much

---

### Post by GWBouge on 2011-06-10
Windows isn't friendly to other OS's.  Simply put, it overwrites Ubuntu's boot loader and doesn't give you any options as to what OS to use.  The whole process is MUCH simpler if you install Windows first.

Preparations for new installs, in short:
1) BACK UP ALL IMPORTANT DATA.
2) Boot up with the Ubuntu LiveCD and use GParted (or whatever bootable partition managers you might have laying around) to create 2 partitions, one ext4 for Ubuntu and one NTFS for Windows
3) Install Windows, THEN Ubuntu.

There's tons of tutorials and How-To's in the forums and on the web as to the specifics of the 3 vague steps listed above, and how to recover the GRUB boot loader if you installed Windows after installing Ubuntu.

---

### Post by nzjethro on 2011-06-10
No worries. If you have any issues, post back. And yeah, if you are willing to lose your Ubuntu setup (or at least if you can back it up then recover it all) I would recommend doing a clean install, XP then Ubuntu so you get Grub working.

+1 GWBouge for that suggestion.

---

