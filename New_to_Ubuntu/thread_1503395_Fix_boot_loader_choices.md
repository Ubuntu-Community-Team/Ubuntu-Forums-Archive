---
title: "Fix boot loader choices?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by FireFreek on 2010-06-06
A while ago I had Windows 7, XP, and Ubuntu on my system. I probably got rid of Windows 7 incorrectly, as the boot loader still remains. The sequence when I start my computer goes like this: Ubuntu bootscreen, where you choose between Ubuntu, or Win 7. If you choose Ubuntu, Ubuntu loads. If you choose 7, it goes to the Windows 7 boot screen. On that, you can choose Windows 7 or an old version of Windows. If you choose Windows 7, it doesn't work, since I no longer have it on the drive. If you choose the other option it will load XP.

Does anyone know how I can change it so it just keeps the ubuntu boot screen letting me choose from windows 7 or XP?

---

### Post by oldfred on 2010-06-06
windows combines its boot loaders into the partition that is active (boot flag). You probably still have win7 files & the XP partition was converted to win7 if you installed win7 after XP.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by FireFreek on 2010-06-07
I'm still confused as to what I can do to fix it though.

---

### Post by oldfred on 2010-06-07
you may need to run the XP repairs. You may have to remove the win7 files from the XP partition first to make sure XP does not see the win7 files, although I think it is 7 that is smart enough to add XP but XP did not know about 7 so it does not add it. Not sure if you are still using the win7 files in the XP partition to boot.

Try XP repairs first. If you run fixMBR it will overwrite grub in the MBR and you will have to reinstall that. But if you want to fully test that winXP boots on its own you may want to run the fixMBR command.

To reinstall grub - besure to reinstall the correct version of grub - grub legacy  0.97 or grub2
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

WinXP repairs:
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild

---

