---
title: "Uninstall ubuntu"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by saicharantej on 2008-12-07
Hi Everyone,

           I've installed ubuntu in dual-boot mode with windows XP being the other operating system.Due to disk usage problems,I need to uninstall ubuntu.Can you please tell me the steps to uninstall ubuntu from my system? 
  
                    Thanks in advance to everyone!!!

---

### Post by billgoldberg on 2008-12-07
> **saicharantej said:**
> Hi Everyone,

           I've installed ubuntu in dual-boot mode with windows XP being the other operating system.Due to disk usage problems,I need to uninstall ubuntu.Can you please tell me the steps to uninstall ubuntu from my system? 
  
                    Thanks in advance to everyone!!!

You just need to format the partition Ubuntu is sitting in to something XP can read and write to (ntfs or fat32) and then repair the xp mbr.

--

You can do the formatting from within Windows and repairing the mbr (master boot record, to replace the grub) can be done with the windows cd.

Guides:

Formatting:
[http://www.ehow.com/how_6026_format-hard-drive.html](http://www.ehow.com/how_6026_format-hard-drive.html)

Reparing the mbr:
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

note: If you do not have the windows cd anymore, you can use the "super grub disk live cd" to do the same.

---

