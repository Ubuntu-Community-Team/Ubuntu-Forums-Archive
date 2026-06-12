---
title: "Windows 7, XP, and Ubuntu GRUB help"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by mattbutsko on 2010-08-07
I just received a 320GB 7200RPM laptop hard drive from eBay. I'm coming from a 120GB 5400RPM hard drive, so naturally this is exciting. I installed XP for Steam gaming since it's lighter than 7, Windows 7 for work and office 2007, and of course Ubuntu for speed, security, and fun because I hate windows.

First I had Grub 2 with the usual linux options, and Windows 7 loader. From Windows 7, I could boot XP or 7. Then, I had to reinstall XP cause I had a botched copy, so I only had XP. Then, I reinstalled Grub 2 using my Ubuntu flash drive, and now I have the usual linux options and Windows XP. Windows 7 is still installed, I didn't touch it and can see the NTFS partition entitled "Windows 7" from Windows XP. Problem is, the GRUB picked up Windows XP and ignored the Windows 7 loader. Anyway, is there any way I can have all three Windows 7, Windows XP, and Ubuntu in the Grub 2 boot loader? If not, how can I replace the Windows XP loader with the Windows 7 loader so I can boot Windows XP from the 7 loader (like my original layout at the beginning of this paragraph)?

---

### Post by oldfred on 2010-08-07
You have to separately install windows to split the boot loaders. I am not sure if you can move boot flag & repair to get each booting separately or not.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You probably have to run the win7 repair tools to get it to become the boot system. When you installed XP was it a primary partition? It may have moved boot flag (active partition) to the XP partition. Move it back to 7 and repair, it will find XP and move XP's boot files to the 7 partition. But then grub will only boot 7 even if it has both entries.

---

### Post by mattbutsko on 2010-08-07
So far the easiest method seems to be to just reinstall Windows 7 so that it'll recognize the Windows XP partition, then reinstall GRUB 2 so that GRUB will see both Linux and the Windows 7 loader, which can boot XP and 7.

---

### Post by wilee-nilee on 2010-08-07
Here is a link to a repair install for W7 that will reinstall the dual boot with XP. 
[http://www.sevenforums.com/tutorials/3413-repair-install.html?ltr=R](http://www.sevenforums.com/tutorials/3413-repair-install.html?ltr=R)

As suggested you also have the boot flag option or a fresh install of W7 using a custom install. If you reinstall W7 build the ntfs partition first with gparted, I had my Ubuntu partitions go unallocated twice when I let the W7 disc build the W7 partition.

---

