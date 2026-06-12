---
title: "GRUB2 - removing bad entry"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by chris59 on 2009-10-31
Hello,

After installing 9.10 I managed to configure GRUB2 according to my needs, but one problem occured.
Let me describe...

Os-prober returns such entries:
```
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain

```Sda1 is the recovery partition. Sda2 is the partition on which Windows7 is installed and also it is set as boot.
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        9572    64598058    7  HPFS/NTFS
/dev/sda3            9573       38913   235681582+   5  Extended
/dev/sda5            9573       18058    68163763+   7  HPFS/NTFS
/dev/sda6           18059       37650   157372708+   7  HPFS/NTFS
/dev/sda7           37651       38779     9068661   83  Linux
/dev/sda8           38780       38913     1076323+  82  Linux swap / Solaris

```After selecting Windows 7 (loader) located on sda2 (partition on which Windows is installed), nothing happens. Windows 7 launches from sda1 (recovery partition). I do not know why, but I do not care - Windows works fine after launching this entry.
So, my GRUB2 list looks as follows:
Ubuntu
Windows 7 (loader) on /dev/sda1 -> works
Windows 7 (loader) on /dev/sda2 -> does not work

Any suggestion how can I remove the 'not working' entry?

---

