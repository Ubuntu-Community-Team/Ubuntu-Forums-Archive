---
title: "Fresh install of Ubuntu on multi-HDD pc..?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by FuneralQueen on 2009-12-31
Hiya

Quick and simple (and probably very obvious) question

I'm looking to install Ubuntu on my PC which has 3 hard drives, at the moment one is for Windows XP, one for media and one for other random stuff. If I install Ubuntu onto the drive that originally had XP - will it wipe out the other drives..? I'm assuming not, however I know how thorough an install of Ubuntu is :)

Thanks!

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
No it will not. You will need to specify that you want to install it into the partition that held XP, an that would be the only thing it touches. I would recommend setting up at least a separate home partition, though.

---

### Post by peakpc on 2009-12-31
It will not wipeout any partition or drive that you do not say for it to during the installation.  Ubuntu has good NTFS read write capabilities. however if your going all ubuntu you could (after installation) backup your data and format to ext3 or ext4.  of coarse backing up all your data before any major install is always a good idea!

---

### Post by LuisGMarine on 2010-01-01
I have a very similar setup. I have 3 hard-drives with Ubuntu, Windows, and media on it's own hard drive.

Pretty sweet because I have windows xp installed on my first hard drive with the windows bootloader still intact.  So when someone turns on my computer like a regular person would, they go straight to windows, like "most" computers these days and they are not aware that there is anything else going on.

For my media, I formated it to FAT so that my Ubuntu and Windows can write to it.  I put my movies, music, pictures etc etc.

Then lastly I got my Ubuntu hard drive, which has the boot loader installed on that hard drive alone, and can only be accessed if I hit "More boot options" in the BIOS when the computer is first starting up.  So if someone where to stumble up until this point they know exactly the goodies they are after =) :guitar:

---

