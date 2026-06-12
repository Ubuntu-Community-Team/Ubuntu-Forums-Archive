---
title: "NTLDR missing"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by jfs35 on 2009-01-30
I have been booting Ubuntu 8.10 off of a corsair flash drive for several weeks. Lately when I try to boot up my desktop PC on Ubuntu I get the message NTLDR is missing hit Ctrl-Alt-Del to reboot. The computer boots up fine on Windows XP. I can use the flash drive to boot Ubuntu successfully on my laptop however. Both run windows XP and I about the same time I had to replace my power supply because the 5VSB buss had erratic voltage. Suggestions?

---

### Post by lykwydchykyn on 2009-01-31
That's typically the error message you see when you try to boot to an NTFS disk that has no OS on it.  Is there another disk/partition on the system with NTFS on it apart from the XP partition?  What filesystem is on the flash drive?

---

### Post by bumanie on 2009-01-31
Please post the output of > sudo fdisk -luNTLDR may be missing or it may be that grub is being pointed at a ntfs data partition with no bootloader on it. Sometimes bios chnages itself around as is pointing to the incorrect hard drive to boot from.

---

### Post by jfs35 on 2009-01-31
Thank you, no, the only partition on the hard drive is for XP. I believe the file system on the flash drive is fat 16 if that is what you mean, although I could be incorrect on that. To get the pc to boot I need to enter the bios and change the first boot device to USB-HDD and it would boot, there are several other USB options. Is it possible that the bios is messed up and I need to use a different option?

---

