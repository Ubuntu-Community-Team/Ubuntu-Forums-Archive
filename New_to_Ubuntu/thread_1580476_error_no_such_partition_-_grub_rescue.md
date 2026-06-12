---
title: "error: no such partition - grub rescue"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by pritzp33 on 2010-09-23
Hi, 
 
I recently installed Ubuntu on my PC that had windows 7 on it. After a while I decided I did not like Ubuntu and decided to uninstall it. I didn't know how to uninstall it and saw on a website that the best thing to do was to go into Windows and delete the partition that had ubuntu on it. This was obviously not the best thing to do because whenever I now start my PC up, it says :
 
error: no such partition.
grub rescue>_
 
It doesn't let me boot from a Windows 7 CD either. It goes back to this screen. I'm not very good with computers so can someone please give me a simple step by step guide on how to fix this? All help appreciated.
 
Thanks, Pritzp33

---

### Post by Rubi1200 on 2010-09-23
Have you set BIOS to boot from the CD (sorry for stating the obvious, but sometimes people forget to do this)?

If you have the Windows 7 CD, you need to reinstall the Windows bootloader to the MBR and the problem should be solved.

---

### Post by drs305 on 2010-09-23
You should be able to restore your Windows with the info in this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

When you deleted the Ubuntu partition the information in the MBR didn't change; it still points to the Grub configuration files in the (now-deleted) Ubuntu partition. You can use the procedures in the above post to restore the MBR to point to your Windows installation.

---

