---
title: "Need help, reformatting Acer Laptop"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Space-Wolf on 2010-01-11
So I figured I'd reformat the HDD using the built in Windows recovery program, thinking it would format the entire drive including Linux and Grub and let me reinstall everything, but grub still loads and now I can't access my windows partition, what happened?

---

### Post by cariboo on 2010-01-11
You probably will have to repair the mbr, if you have a Windows install disk, it is just a matter of booting into the recovery console, and running fixboot and fixmbr. From the sounds of it, you just have a restore partition. To get into the recovery console with an install disk

If you don't have an install disk you can install the recovery console following these instructions.

[list=1]
[*]Click Start, and then click Run.
[*]In the Open box, type d:\i386\winnt32.exe /cmdcons where d is the recovery partition.
[*] Reboot when done, on reboot you should see a recovery console selection in the Windows boot menu.
[/list]

---

