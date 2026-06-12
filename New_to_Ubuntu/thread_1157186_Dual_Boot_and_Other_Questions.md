---
title: "Dual Boot and Other Questions"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Daveee6 on 2009-05-12
So I have been researching ubuntu and I have decided I wanted to convert from vista. Right now I would like to learn more about ubuntu so I decided I would do a dual boot with vista and ubuntu. It seems easy enough but I was wondering if I will be able to access all of my files on both operating systems (word documents I have saved, music, pictures, videos, etc...). I am going to partition the disk...one for ubuntu the other for vista. My other question is will I have any of my programs like thunderbird or firefox that I already have running on vista? Thanks for all of your help!!

---

### Post by Dynaflow on 2009-05-12
Linux is able to read the Windows filesystems, so you should be able to read and write files in your Windows partition from Linux.  However, Windows will only recognize a small range of (Microsoft) filesystems, and so Windows won't even be aware that the Linux partition is there.  Firefox and Thunderbird have native versions in Linux.

---

### Post by AndyCooll on 2009-05-12
As Dynaflow says.

You can find a list of Linux alternatives to apps that you are probably used to here: [Linux Alternative Project]("http://www.linuxalt.com/"). Having said that, many apps are cross platform anyway (e.g. Firefox, Thunderbird, Open Office.org, Vuze), so you might already be familiar with the best known ones.

:cool:

---

### Post by Jon Monreal on 2009-05-12
> **Dynaflow said:**
> Linux is able to read the Windows filesystems, so you should be able to read and write files in your Windows partition from Linux.  However, Windows will only recognize a small range of (Microsoft) filesystems, and so Windows won't even be aware that the Linux partition is there.  Firefox and Thunderbird have native versions in Linux.

If you wanted, you could create a FAT32 partition for all of your files that could be used by both Windows and Linux. For programs, you will of course have to use Linux equivalents.

If you need help with this, feel free to ask. It is easier than you might think to use Vista to shrink your Windows partition, and then use Ubuntu (the LiveCD is the easiest at this) to create both a partition for Ubuntu and a FAT32 partition for all your files.

-Jon

---

### Post by Dynaflow on 2009-05-12
> **Jon Monreal said:**
> If you wanted, you could create a FAT32 partition for all of your files that could be used by both Windows and Linux. For programs, you will of course have to use Linux equivalents.

If you need help with this, feel free to ask. It is easier than you might think to use Vista to shrink your Windows partition, and then use Ubuntu (the LiveCD is the easiest at this) to create both a partition for Ubuntu and a FAT32 partition for all your files.

-Jon

True; however, FAT32 has some ... well ... [limitations]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32").

If you really anticipate switching back and forth between OS'es this much, I would install ntfs-3g , enable it (once installed, just open the program under System -> Administration -> NTFS Configuration Tool, and tick the boxes), and set your primary "saving stuff" directory to your Windows My Documents folder.  You can add a link to it inside your Home folder or on your desktop.

NTFS, the filesystem your Windows installation floats on, is rather more robust and featureful than FAT32, though nowhere near EXT3, which is the filesystem your Ubuntu installation should use by default.

The command to install ntfs-3g is ```
sudo apt-get install ntfs-3g
```

---

### Post by Jon Monreal on 2009-05-12
> **Dynaflow said:**
> True; however, FAT32 has some ... well ... [limitations]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32").

If you really anticipate switching back and forth between OS'es this much, I would install ntfs-3g , enable it (once installed, just open the program under System -> Administration -> NTFS Configuration Tool, and tick the boxes), and set your primary "saving stuff" directory to your Windows My Documents folder.  You can add a link to it inside your Home folder or on your desktop.

NTFS, the filesystem your Windows installation floats on, is rather more robust and featureful than FAT32, though nowhere near EXT3, which is the filesystem your Ubuntu installation should use by default.

The command to install ntfs-3g is ```
sudo apt-get install ntfs-3g
```

A good idea. To tell you the truth I've always used FAT32 because it works well with OSX as well. I simply don't usually deal with files that violate the limitations. And, call me old fashioned, but I'm not a big fan of NTFS.

At any rate, for your purposes I would recommend NTFS, even more so if you like to store movies on your computer that you rip from DVDs or the like. These can violate the limits for size in FAT32.

---

