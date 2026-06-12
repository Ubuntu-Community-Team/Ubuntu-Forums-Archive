---
title: "Cannot install Lubuntu. Parted gives error messages."
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Toolless on 2011-04-26
Having some probles installing from hard drive on the lubuntu instalation menu
I select 'install the program' and i dont get anything about formating or partisioning it just goes stright to the desk top and hangs
So I re did it and this time from the boot menu selected 'try lubuntu'
Was told to go to the terminal and put the following in and this is the resaults

__________________________________
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo parted --list
Error: Can't have a partition outside the disk!                           

Model: ATA ST33210A (scsi)
Disk /dev/sdb: 3249MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  3245MB  3245MB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
Ignore/Cancel? ignore                                                     
Backtrace has 14 calls on stack:
  14: /lib/libparted.so.0(ped_assert+0x2a) [0x12087a]
  13: /lib/libparted.so.0(ped_geometry_read+0x116) [0x12a5e6]
  12: /lib/libparted.so.0(hfsplus_probe+0x3a1) [0x14a751]
  11: /lib/libparted.so.0(ped_file_system_probe_specific+0x6c  ) [0x1223dc]
  10: /lib/libparted.so.0(ped_file_system_probe+0x81) [0x1229d1]
  9: /lib/libparted.so.0(+0x4e783) [0x165783]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x1297d5]
  7: parted() [0x804db58]
  6: parted() [0x804ece3]
  5: parted() [0x8050ffa]
  4: parted() [0x8052671]
  3: parted(main+0x2e) [0x805277e]
  2: /lib/libc.so.6(__libc_start_main+0xe7) [0xd6ece7]
  1: parted() [0x804bbb1]
Aborted (core dumped)
____________________________

Its all dobble dutch to me but it says
Error: Can't have a partition outside the disk!                           
and
Warning: The driver descriptor says the physical block size is 512 bytes, but
 Linux says it is 2048 bytes.

So it seams like there is a hard drive and memory issue hear

Hear is the link to the starter thread
[http://ubuntuforums.org/showthread.php?t=1737450](http://ubuntuforums.org/showthread.php?t=1737450)

Thanks
Toolless

---

### Post by mörgæs on 2011-04-26
First let us hear what you are trying to achieve. Only Lubuntu on the machine? 

A full description of the hardware would also help.

---

### Post by Toolless on 2011-04-26
Im trying to install this program as an OS when I boot the machine up
I wolud like to have 2 partisions on my master hard drive; my current win xp which im running now and the lubuntu OS shown below
I dont want any other OS installed which includes the slave

[IMG]http://i291.photobucket.com/albums/ll319/Batista230/ubuntu.jpg[/IMG]
From this link  [http://lubuntu.net/](http://lubuntu.net/)
(do know how to link it in BBC)

And my computer is
[IMG]http://ebayphotos.webs.com/linux/15.jpg[/IMG]
[IMG]http://ebayphotos.webs.com/linux/16.jpg[/IMG]
[IMG]http://ebayphotos.webs.com/linux/17.jpg[/IMG]
[IMG]http://ebayphotos.webs.com/linux/18.jpg[/IMG]
[IMG]http://ebayphotos.webs.com/linux/19.jpg[/IMG]

---

### Post by mörgæs on 2011-04-26
First step concerns Windoze: 

Delete all unneeded files from Windoze, including what is in the trashcan.

Run Scandisk and Defragment a couple of times.

In Windoze, shrink the space allocated in order to give space for Ubuntu. Keep some empty space left for Windoze, though.

Write again when this is done. Check that Windoze runs as normal.

---

### Post by crispy_420 on 2011-04-27
In Windows try cleaning some space with CCleaner and select the option to remove hotfix backups. This should give a ton of space. Also remove the temp files created when installing service packs should recover a few hundred MB. It is a hidden file in the Windows directory (C:Windows). Also the is a great program called WinDirStat that analyzes the drive and shows what is using the space visually so you can decide how slim it down.

---

### Post by Toolless on 2011-04-27
It could be verry well the fact that lubuntu wont installl on a hard drive with OS system on 
And can not create a patision for its self

But I will dig out another hard drive later and try it on that

> **mörgæs said:**
> 
Delete all unneeded files from Windoze, including what is in the trashcan.

There are none reley everthing I need is on my slave the primary hard drive is almost emety

> **mörgæs said:**
> 
 Run Scandisk and Defragment a couple of times.
Did that last week when i was fixing some hard drive

> **mörgæs said:**
> 
In Windoze, shrink the space allocated in order to give space for Ubuntu. Keep some empty space left for Windoze, though.
How do I do this 
Do I have to boot up pc with the win xp disk in or something



> **crispy_420 said:**
> In Windows try cleaning some space with CCleaner and select the option to remove hotfix backups.
CCleaner and hotfix backups?
What are these well there certainly not on my pc coz i did a search for them

> **crispy_420 said:**
> 
 This should give a ton of space. Also remove the temp files created when installing service packs should recover a few hundred MB. It is a hidden file in the Windows directory (C:Windows). 
I see there is index.dat for cookies and history and internet fles
I sopose all the temp intewrnet files want rid of

> **crispy_420 said:**
> 
Also the is a great program called WinDirStat that analyzes the drive and shows what is using the space visually so you can decide how slim it down.
Where can i get this program for Free?

Thanks
Toolless

---

### Post by mörgæs on 2011-04-27
Have you done everything you can, including intense googling, to find the answers?

---

### Post by crispy_420 on 2011-04-27
I would not recommend anything but free software if possible and both of these are free of cost.

You have XP installed on the machine right? Boot into it and download the needed software:

CCleaner: [http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)
WinDirStat: [http://windirstat.info/](http://windirstat.info/)

Install both or if you choose, get the portable versions that do not need installation.

When you open CCleaner it defaults to the cleaning screen. At the bottom of the listed options for cleaning is "remove hotfix installers" (or something similar). Review your choices (it will wipe all browser history) then select analyze. After a few minutes (depending on how much data and PC speed) it will show you how much it can remove. If satisfied select "Clean" and you will get that space back.

Make sense?

There are other options too but that would require a few things: comfort in knowing XP intimately enough to know what is safe to remove and much more explanation.

---

### Post by crispy_420 on 2011-04-27
How to remove XP Service Pack backup files:

[http://webtrickz.com/how-to-remove-files-backed-up-by-windows-xp-sp3/](http://webtrickz.com/how-to-remove-files-backed-up-by-windows-xp-sp3/)

This will recover a few hundred MB. Also many software vendors create temp files in the root of the C: drive for their installers, many can be easily removed to recover space.

---

### Post by Toolless on 2011-04-27
> **crispy_420 said:**
> How to remove XP Service Pack backup files:

[http://webtrickz.com/how-to-remove-files-backed-up-by-windows-xp-sp3/](http://webtrickz.com/how-to-remove-files-backed-up-by-windows-xp-sp3/)

This will recover a few hundred MB. Also many software vendors create temp files in the root of the C: drive for their installers, many can be easily removed to recover space.

Have just checked the windows folder and there are no backup files present

---

### Post by crispy_420 on 2011-04-28
Did you enable viewing of hidden and system protected files? They will not be visible otherwise. If you followed the CCleaner guide all of the $kb (Windows Hotfix aka Updates) should be gone. The service pack folder should be called $ServicePack.....

---

