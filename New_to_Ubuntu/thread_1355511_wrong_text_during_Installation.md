---
title: "wrong text during Installation"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Adi100 on 2009-12-15
mine was  xp and win7 Rc dual boot configuration.
 I restored xp MBR and Boot code using Xp installation media and installed the UBUNTU9.10. on partition , where win 7 was installed.

- during the  installation process when you manually configure your partitions  UBUNTU setup continues to detect Xp as win7.

-Not only this after installation, when computer reboots it is  presenting a boot menu showing win7 loader(sda1), 

I think UBUNTU should have used more generic names like Windows instead of Windows 7 loader , As my computer does not have windows 7.

regards

Adi

---

### Post by mikewhatever on 2009-12-15
Windows usually puts its boot loader files on the first primary partition, so that if XP was installed first, and W7 after it, chances are, W7's boot loader is still on C:\, although W7's partition has been deleted. On the other hand, you can modify GRUB's menu to show what entries you like. Last, but not least, Ubuntu installer doesn't care about what kind of Windows is installed on which partition, and if any at all. The installer works from the CD and doesn't rely on Windows. Either way, those are not Ubuntu problems.

---

