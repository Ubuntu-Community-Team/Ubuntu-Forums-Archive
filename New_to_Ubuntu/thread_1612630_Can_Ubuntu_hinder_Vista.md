---
title: "Can Ubuntu hinder Vista"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Snake4eva on 2010-11-03
I have just installed ubuntu 9.04 desktop edition on a 140 GB hardrive with windows vista. Vista was installed first then I used vista's shrink tool to split the drive (110 GB for Vista and 30 GB for Ubuntu 9.04). Grub is in the MBR while vista is below it. I am new to linux; this is my first use or instalation. Since I installed Ubuntu some of my vista programs, adobe acrobat reader in particular, has been malfunctioning.I was just wondering if this is because vista's bootloader isn't in the MBR.

---

### Post by Quackers on 2010-11-03
Welcome to UF.
Once the MBR has done its bit in the loading of the OS it takes no further part. It certainly won't affect a program installed inside Windows.

---

### Post by Mark Phelps on 2010-11-03
One of the standard pieces of advice we give is that, after you shrink the Vista/Win7 partition, you boot back into it a couple of times to let the filesystem do any resynching stuff it needs.

IF you didn't do that, there may be some leftover filesystem peoblems from the shrinkage that is now giving you problems.

To address that possibility, next time you're in Vista, select the option to check the filesystem upon reboot and let it run chkdsk to completion.

IF you still have problems after that, they're not related to your Ubuntu installation in any way.

---

### Post by TBABill on 2010-11-03
Vista doesn't rely on the Windows boot loader. You are able to use other boot loaders and Grub2 is just another. If your Vista install is having issues it would more likely be related to the partitioning that was done rather than the fact that you are booting from another boot loader.
 
Out of curiosity, why did you choose Ubuntu 9.04? It's support ended already and currently supported systems are 8.04 till April, 9.10 till April, 10.04 till April of 2013 and 10.10 till April 2012. There will be no more updates to 9.04. Just food for thought if nothing else.

---

### Post by Snake4eva on 2010-11-03
Thanks I'll try it when I go home.

---

### Post by Mark Phelps on 2010-11-03
> **TBABill said:**
> Vista doesn't rely on the Windows boot loader.

Since when?  Are you NOT familiar with the role of BOOTMGR and its pals?

All that GRUB does is hand off control to a partition containing a Windows Boot Loader.  If that partition doesn't have one, Windows does not boot.

---

