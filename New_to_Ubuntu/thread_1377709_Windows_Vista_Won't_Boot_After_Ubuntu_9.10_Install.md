---
title: "Windows Vista Won't Boot After Ubuntu 9.10 Install"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by ExcellentEngineer on 2010-01-10
Hello Everyone,

I have a slight problem. I have a computer that I built myself. It has in this order the following operating systems:

Windows XP Professional x32 -> Windows XP Professional x64 -> Windows Vista Business x64 -> Ubuntu 9.10 x64

I installed up to Windows Vista Business x64 with not problems. I could boot all three operating systems. I then installed Ubuntu 9.10 and it works fine. The GRUB gives me the option of booting into Windows Vista but if I select this option, the system just restarts and returns to the GRUB menu.

---

### Post by lindsay7 on 2010-01-10
Boot into Ubuntu and try this, type sudo update-grub in the terminal and see if that will fix the problem.

---

### Post by ExcellentEngineer on 2010-01-11
> **lindsay7 said:**
> Boot into Ubuntu and try this, type sudo update-grub in the terminal and see if that will fix the problem.

Thanks for the info. No luck with that I'm afraid. Any other suggestions?

---

### Post by oldfred on 2010-01-11
Are you sure your windows boot is from Vista? Windows combines its boot into the first install of windows that has the boot flag on. All the other windows cannot be independently booted by grub.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

It may be possible to move the boot flag & repair a windows install, then reinstall grub. But I have not tried that.

---

### Post by ExcellentEngineer on 2010-01-12
> **oldfred said:**
> Are you sure your windows boot is from Vista? Windows combines its boot into the first install of windows that has the boot flag on. All the other windows cannot be independently booted by grub.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

It may be possible to move the boot flag & repair a windows install, then reinstall grub. But I have not tried that.

Thanks for the info. I will try that later on and let you know how it worked. To answer your question, yes, I'm sure all my Windows boots are controlled from Vista. Prior to installing Ubuntu, the Windows Vista bootloader would appear with the option of starting Windows Vista or "Older Versions of Windows". Selecting the "olver Versions" option would then boot into the legacy Windows bootloader with the option of booting XP x32 or XP x64. All three versions of Windows coulb be successfully booted.

---

### Post by philinux on 2010-01-12
> **ExcellentEngineer said:**
> Thanks for the info. I will try that later on and let you know how it worked. To answer your question, yes, I'm sure all my Windows boots are controlled from Vista. Prior to installing Ubuntu, the Windows Vista bootloader would appear with the option of starting Windows Vista or "Older Versions of Windows". Selecting the "olver Versions" option would then boot into the legacy Windows bootloader with the option of booting XP x32 or XP x64. All three versions of Windows coulb be successfully booted.

Another option would be to use easybcd.

I use this on my gf's vista laptop to boot into linux. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by oldfred on 2010-01-12
Which partition has the boot flag as that is the windows partition that windows actually uses to boot?

Grub can turn (or make windows think it is turned on) the boot flag with the makeactive. I am not sure it is required or not once grub has jumped to the windows partition to boot.

You can also look at the boot.ini file in XP to see if it lists more than one windows.

---

