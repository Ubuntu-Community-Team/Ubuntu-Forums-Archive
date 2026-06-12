---
title: "Make my external hard drive writable?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Jimleko211 on 2009-07-26
I purchased an external hard drive today, and it was working well until I went in and messed with the file system.  I used Gparted to make it a ext4...only I stopped halfway through.  Then, figuring it would solve the problem of my disc being unwritable, I formatted it again to ext3, allowing it to go all the way.

Gparted says that 9.55gb is used, while Nautilus says that 16kb is taken up, with the note "some contents unreadable".

---

### Post by northern lights on 2009-07-26
If it is correctly formatted, the following will sort you out```
sudo chown -R USERNAME:USERNAME /media/DISK && chmod -R 770 /media/DISK
```where USERNAME needs to be replaced by your username and DISK by the appropriate location.

If it isn't or your uncertain, please post the output of ```
sudo fdisk -l
```

---

### Post by Paddy Landau on 2009-07-26
If there is no data on the external hard drive, then I suggest that you start again.

[LIST]
[*]Go back to gparted.
[*]Delete the partition. (Careful... Make sure it's your external hard drive and not your working disk!)
[*]Recreate the partition and format.
[/LIST]

---

### Post by jward3010 on 2009-07-26
Realistically, consider leaving the external hard drive as NTFS as it's most compatible with all systems you'll bring it to. ext4 and 3 are better filesystems; faster, less fragmentation, more efficient, better security for files and mishaps but they're compatiblity in the wider Windows world is non-existent unforunately. If this ain't a problem for you then go for it.

If the above techniques ain't working for you, hopefully someone can can come up with a command for destroying and re-writing the partition table, that will start you from absolute scratch. In fact you can do it within GParted, select the drive from the list and then click on "Device" menu, select "Create Partition Table" and choose default of "msdos".

---

### Post by jward3010 on 2009-07-26
Realistically, consider leaving the external hard drive as NTFS as it's most compatible with all systems you'll bring it to. ext4 and 3 are better filesystems; faster, less fragmentation, more efficient, better security for files and mishaps but they're compatiblity in the wider Windows world is non-existent unforunately. If this ain't a problem for you then go for it.

If the above techniques ain't working for you, hopefully someone can can come up with a command for destroying and re-writing the partition table, that will start you from absolute scratch. 

Hold the phone! In fact you can do it within GParted, select the drive from the list and then click on "Device" menu, select "Create Partition Table" and choose default of "msdos".

---

### Post by Liolikas on 2009-07-26
FAT32 is most compatible. USB flash drives and mp3 players use FAT32. You will have big problems if try ntfs on MACOS

---

