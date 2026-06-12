---
title: "dual boot ubuntu 10.04 and windows xp"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by vinaceous on 2010-06-03
Hello,

I have been playing with Ubuntu for couple of months. I did something different this time and is annoying me now.

I had Windows 7 and Windows XP on my laptop dual booted. The bootloader is configured to Win 7. I removed Win7 (formatted the partition) and installed Ubuntu. I could not find a way to add Win XP to the boot menu. I did it in Fedora and worked fine. Win XP is in sda5 partition on the same hard drive.

Ubuntu 10.04 was installed with Grub2, so I downgraded to grub legacy (since grub2 is beta). I tried searching for a solution. The /boot/grub folder does not have menu.lst file. In the legacy one, I found grub.cfg but I cannot edit the file.

I backed-up the files in windows xp but I cannot lose the settings and installations. I did set it for programming use. Please help me solve this issue.

Thanks in advance.
Vin

---

### Post by oldfred on 2010-06-03
Windows just about has to boot from a primary partition. I have seen one or two exceptions but not easy and I do not know how.

You should have installed windows to a primary. If you have a primary still available you may be able to put the boot files there and then be able to boot the windows in sda5.

If you have space you may be able to move the windows install to a primary but some windows files will have to be repaired.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Some info on extended:
Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

---

### Post by vinaceous on 2010-06-05
Hello oldfred,

Thank you for the reply. I've been reading from the links you posted. I tried one of them that edited the 40_custom file in the grub.d folder. It only displayed the option in the boot menu but is not booting into win xp. I believe the boot loader for xp has been damaged. I didn't want to reinstall xp. I can repair but the disk could not find the hard drive. The xp (sda5) is hidden behind the extended partition of the same size (sda2).

Is there any way to fix this? Keeping Ubuntu in primary and win xp in logical.

Just a reminder from my previous post- I formatted and installed Ubuntu, removing Win 7 (on sda1) which is holding the bootloader. The win7 bootloader was deleted and now xp could not boot. I could not find a way to include windows xp in grub or get it work.

--Vin

---

### Post by oldfred on 2010-06-05
Then you have things backwards. Ubuntu does not care if it is in a primary or logical partition inside the extended. Windows will not boot from a logical partition. You can only install a second version of windows in a logical partition if you have a windows in a primary and it combines its boot so the install in the logical is actually booting thru the primary partition.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

HOWTO: Moving/Copying Windows XP to another Partition 
[http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146)

You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)
[http://support.microsoft.com/kb/306559#f1](http://support.microsoft.com/kb/306559#f1)

---

### Post by vinaceous on 2010-06-05
Thanks Fred. I got my XP back as it is. In the process I had to comlpletely delete/format the ubuntu OS. I installed the same copy of XP in C: as it is in D:. Rebooted using the boot disk > entered into recovery console. It did show both installations of XP. I logged into the new installation> bootcfg /add > included the xp in D: and run fixmbr d:. Reboot and it worked.

Now I used the file and settings transfer wizard, copied all the files and settings of xp in D: to c:. And it is done. Now both the copies of XP are like mirror images.

Now I have to try and install ubuntu in d:.

What I did before was a total dumb thing but I just wanted to see what happens and the bright side is, I found a fix.

Some of the links really helped. Thank you.

--Vin

---

