---
title: "Install Problem"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sjmcyyc1960 on 2009-03-06
I have been trying solve this for a week, any help would be appreciated. My system has 2 hard drives, a 320GB ide drive which has vista installed on it, and a 500GB SATA which has nothing installed on it. When I installed Ubuntu 8.10, I installed it inside windows, and the system rebooted there was no dual boot to choose OpSys, it went straight to Vista. I then set up Linux partitions on the 500GB SATA and installed it fully, still no boot choice, straight to windows. If I change the boot order in the BIOS to boot from the 500GB first, I do get the dual boot choice and can boot into Ubuntu, but the Vista choice does not work. From what I can tell Ubuntu is assuming that my 500GB SATA is the boot drive. Is there any way I can cahnge this while it is installing or do I have to do something else? This is driving me crazy because I installed Ubuntu on another computer with a very similar setup and had no trouble....please help.

Thanks
Sean

---

### Post by Vonnick on 2009-03-06
I believe the dual boot menu will only show both Windows and Ubuntu if the two are on the same HDD.

---

### Post by davec64 on 2009-03-06
I suspect you've installed GRUB to the MBR of the linux disk, so when you set to boot the windows disk you don't get the GRUB menu.

I suggest you set the boot order in the bios to boot the Linux disk and edit your Grub file so it points to the windows disk.

Here's an old tutorial on how to set up your disks and Grub, it's for XP so you might have to google for any differences for Vista if it doesn't work:

[http://www.ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives]("http://www.ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives")

Hope that helps! :)

---

