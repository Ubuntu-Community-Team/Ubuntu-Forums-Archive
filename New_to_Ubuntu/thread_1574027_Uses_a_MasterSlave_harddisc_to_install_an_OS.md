---
title: "Uses a Master/Slave harddisc to install an OS?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by mastermael on 2010-09-13
I don't know if this is possible, If it is Advice on the most efficient way to do it. I know how to connect the discs, I just don't know how to go about this this.

---

### Post by amjjawad on 2010-09-13
> **mastermael said:**
> I don't know if this is possible, If it is Advice on the most efficient way to do it. I know how to connect the discs, I just don't know how to go about this this.

It's advisable to install an OS on a Master HDD. Whether you have IDE or SATA, it's better to set the jumper for your IDE HDD to Master and install. With SATA, you don't need to set any jumper, just make sure your BIOS is detecting your SATA HDD as Master.

After all, check your BIOS to know which HDD is Master.

If you have a laptop, then you would have only 1 HDD (internal) and it's definitely Master.

Good Luck!

---

### Post by cariboo on 2010-09-13
That's kind of bad info, the operating system can be installed on any hard drive whether it's a master or a slave. Windows needs the bootloader to be on the first partition of the first hard drive, you can put the rest of the os, anywhere you want.

Linux doesn't care where you install it, as long as grub2 is installed on the mbr of the first hard drive.

I have 5 OSs installed on one system, XP, Maverick, PCLinuxOS, Fedora and openSUSE, XP is installed on the first hard drive as it's only a 30Gb drive. the rest are installed on 9 partitions on the second drive. They are all booted from Maverick's grub2 menu.

---

### Post by amjjawad on 2010-09-13
> **cariboo907 said:**
> That's kind of bad info, the operating system can be installed on any hard drive whether it's a master or a slave. Windows needs the bootloader to be on the first partition of the first hard drive, you can put the rest of the os, anywhere you want.

Linux doesn't care where you install it, as long as grub2 is installed on the mbr of the first hard drive.

I have 5 OSs installed on one system, XP, Maverick, PCLinuxOS, Fedora and openSUSE, XP is installed on the first hard drive as it's only a 30Gb drive. the rest are installed on 9 partitions on the second drive. They are all booted from Maverick's grub2 menu.

I didn't say it's a must, I just said it's advisable :P
But that's great to know, thanks for the info :)

5??? what are you doing with all of them? just curious :P

---

### Post by sandyd on 2010-09-13
> **amjjawad said:**
> I didn't say it's a must, I just said it's advisable :P
But that's great to know, thanks for the info :)

**5??? what are you doing with all of them**? just curious :P
even I,  the amazing distro hopper don't have that many.....
I only have windows 7 and gentoo along with lots of virtualboxes....

---

### Post by mastermael on 2010-09-14
> **cariboo907 said:**
> That's kind of bad info, the operating system can be installed on any hard drive whether it's a master or a slave. Windows needs the bootloader to be on the first partition of the first hard drive, you can put the rest of the os, anywhere you want.

Linux doesn't care where you install it, as long as grub2 is installed on the mbr of the first hard drive.

I have 5 OSs installed on one system, XP, Maverick, PCLinuxOS, Fedora and openSUSE, XP is installed on the first hard drive as it's only a 30Gb drive. the rest are installed on 9 partitions on the second drive. They are all booted from Maverick's grub2 menu.

> **amjjawad said:**
> It's advisable to install an OS on a Master HDD. Whether you have IDE or SATA, it's better to set the jumper for your IDE HDD to Master and install. With SATA, you don't need to set any jumper, just make sure your BIOS is detecting your SATA HDD as Master.

After all, check your BIOS to know which HDD is Master.

If you have a laptop, then you would have only 1 HDD (internal) and it's definitely Master.

Good Luck!

I worded this horribly. Is it possible to use a master postition harddisc to install an OS the onto the slaved harddisc?

---

### Post by oldfred on 2010-09-14
If you are using grub2 you can boot the ISO directly from your hard drive. The slave drive would not be directly bootable unless you install in another computer or make it master. If another computer do not install proprietary video drivers and it should boot. Be sure to used advanced button so grub is on slave drive.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different unmounted  partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

