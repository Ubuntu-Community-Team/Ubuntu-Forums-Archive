---
title: "Corrupted file system on NTFS partition."
date: 2009-09-13
forum: New to Ubuntu
---

### Post by zedi on 2009-09-13
Mine Winblows NTFS partition is complete cactus. I had BSOD: Unmountable-Boot-Volume error, and now I can not access it. Ubuntu can not mount it; tells me to do `chkdsk /f` - file system is corrupted (the same gparted and Live CD). But I can't boot Winblows, not even `safety mode with command prompt` - it gives me BSOD. According to Goggle, remedy is Recovery Mode from installation disk & `chkdsk /r`, but it doesn't work for me. I've got prompt C: - but it's doing chkdsk on D: - which is my second drive formated in FAT32. When I tried `bootcfg /rebuild` in Recovery Mode it said something like: C: directory doesn't exist or is corrupted.
I've kept my photos on Wins partition and I didn't backup recent ones, so if anybody knows how to access bloody thing it would be fantastic, but it looks like only way out of this mess is re-installation of Winblows XP. 
Now, will I be able to access mine Jaunty and Intrepid? Will Grub still be OK? And if not, what I have to do to fix it? I heard about Super Grub Disk, but I'm a bit afraid of it. I'm not very good with command line. Is there a GUI way to fix Grub?
The reason I want Winblows is: I bought KaiserBaas USB device to convert mine VHS collection to digital and that's what I was doing when BSOD happened. Unfortunately Ubuntu can't see mine USB device and there is no driver for Linux on disk (only Wins & Mac). Is there any way to capture video from mine KaiserBaas on Ubuntu?

---

### Post by zephyrcat on 2009-09-14
Sounds like you need to tell chkdsk what drive to work on. For example:

chkdsk c: /f

Taken from:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by zedi on 2009-09-15
ZephyrCat,
                  Unfortunately, even when I tell chkdsk what drive to work on ( chkdsk c: /f ) it's still doing check on drive D: - looks like it can't see drive C:, at all. For DOS in  Recovery Mode mine NTFS partition doesn't exist. Could it be, because mine FAT 32 disk is set in BIOS as first hard drive (sdba)? Just thought...?????????????????????????????????????????????????????????????????

---

### Post by foxmulder881 on 2009-09-15
Sounds like your c: hard drive is borked. Does Ubuntu recognize its presence?

---

### Post by zedi on 2009-09-15
foxmulder881,
I don't think so, it is the same hard drive where Ubuntu resides and – yes Ubuntu recognise its presence, but can't mount it, not even from Live CD.

---

### Post by foxmulder881 on 2009-09-15
> **zedi said:**
> foxmulder881,
I don't think so, it is the same hard drive where Ubuntu resides and – yes Ubuntu recognise its presence, but can't mount it, not even from Live CD.

So you simply have a corrupt partition, that's all. Boot into the Ultimate Boot CD and use of the partitioning tools and completely format the corrupted partition.

---

### Post by zedi on 2009-09-16
foxmulder881,
Formating will be mine last option. I'm still hopping somebody comes up with better solution and you didn't tell me how reinstalling Winblows affects Grub?

---

### Post by expatCM on 2009-09-16
I have not tried it out but I have read a lot of discussion about the use of ddrescue to help at least recover the data.  Perhaps this could help you out ...........
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)
I think there are quite a few threads on this topic if you need to follow up in better detail.

---

### Post by zedi on 2009-09-16
expatCM,
I'm going to have a look `ddrescue`. Thank you for advice!
Anybody – how to reinstall Winblows and still have access to Ubuntu??????????

---

### Post by oldfred on 2009-09-16
Have you tried testdisk - it supposedly recovers damaged partitions or data from those partitions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

In Synaptic it says this about testdisk:
It is very useful in recovering lost partitions.
so you can easily download it.

To restore various boot loaders
[SIZE=2]**[COLOR=blue]How to restore the Ubuntu/XP/Vista bootloader.[/COLOR]**[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by zedi on 2009-09-16
oldfred,
Your suggestions look promising. Thing is, I'm very busy next couple days, but I definitely will tray to learn both: ` testdisk` and ` How to restore the Ubuntu/XP/Vista bootloader`.
Thanks, merci beaucoup, danke, spasiba, dziekuje etc..

---

