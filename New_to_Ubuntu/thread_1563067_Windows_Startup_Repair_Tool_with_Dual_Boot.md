---
title: "Windows Startup Repair Tool with Dual Boot?"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by nash black on 2010-08-28
Hi

I am running XP pro SP3 in a dual boot with the latest Ubuntu. Ubuntu has been great, but Windows has been acting up. It frequently has "STOP : 0000000F4..." errors causing the system to shut down. 

After doing some research, I have found that this error sometimes occurs in multi-hard drive systems and can be repaired with the Windows Startup Repair Tool. My only concern is whether or not using this tool on a dual-boot will play well with GRUB and my Ubuntu partition.

Does anyone have experience/ insights with that tool or this problem?

Thanks
Nash

---

### Post by oldfred on 2010-08-28
If you have two drives do you have windows boot loader in one and grub in the other. Then you will have no issues.

If you have grub in the MBR of the windows drive then you may have to reinstall grub. 

If you have the liveCD it is relatively easy to just reinstall grub or grub2, just be sure which you have.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

