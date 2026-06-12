---
title: "I broke it, need a little help"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-04-01
I've been running Maverick on a 64 bit HP G62 since December.  It's a "multi boot" machine, still has windows 7 on it, Edubutnu 10.10 because I'm a teacher and wanted to check it out, plus Maverick.  I decided to dump windoze and Edubuntu, leave Maverick on and try the Natty Beta where Edubuntu used to be.

I screwed something up.  Not sure what.  Went in to windoze, made sure I hadn't left anything behind that I needed, used the mini partition tool while I was in there to delete edubuntu and merge some unallocated space.  My intention was to split the drive (320 Gb) in two, Natty Beta on the front half, leave Maverick where it was on the aft half. 

Did a reboot, apparently I screwed the MBR, because now I all I get is grub rescue>

I used the live CD (Natty beta 1), went into terminal, 
```

sudo apt-get install lilo
sudo lilo -m /dev/sda mbr

```

Which is what I was advised to do back when I started on Ubuntu and somehow ended up in Wubi with no MBR.  It didn't help this time, I was right back into grub rescue.

<thinks> "No problem, I'll copy my files (docs, music) onto a couple of big fat thumb drives, then wipe the whole show and jump into Natty with both feet.

So here I am, I can't fix the MBR, I can't copy my files from the Maverick installation because I don't have necessary permissions.  The music I can mostly reinstall, but my students grades are in the docs folder.  Yes, I normally have a backup, but I had a wee heart attack last week and never quite got around to doing the backup.  Yes, I'm a bit of an idiot for that, thankyewverymuch.

Any ideas?  I have no problem wiping everything, but if I lose those grades life is going to be uncomfortable for a while.

regards, Richard

---

### Post by Robing Goodfellow on 2011-04-01
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f17b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       13710   109919825    7  HPFS/NTFS
/dev/sda3           13711       38901   202338305    f  W95 Ext'd (LBA)
/dev/sda4           38901       38914      105816    c  W95 FAT32 (LBA)
/dev/sda5           21005       38169   137865216   83  Linux
/dev/sda6           38169       38901     5878784   82  Linux swap / Solaris


```

and

```

 sudo LANG=C sfdisk -d /dev/sda 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   407552, Id= 7, bootable
/dev/sda2 : start=   409600, size=219839650, Id= 7
/dev/sda3 : start=220252158, size=404676610, Id= f
/dev/sda4 : start=624928768, size=   211632, Id= c
/dev/sda5 : start=337438720, size=275730432, Id=83
/dev/sda6 : start=613171200, size= 11757568, Id=82


```

then finally

```

sudo parted -l
Model: ATA SAMSUNG HM321HI (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  210MB  209MB   primary   ntfs            boot
 2      210MB   113GB  113GB   primary   ntfs
 3      113GB   320GB  207GB   extended                  lba
 5      173GB   314GB  141GB   logical   ext4
 6      314GB   320GB  6020MB  logical   linux-swap(v1)
 4      320GB   320GB  108MB   primary   fat32           lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label      

```

before anybody asks

regards, Richard

---

### Post by Phil D. on 2011-04-01
[Fix GRUB with LiveCD]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/")
This should help. Because Lilo is no longer used.

Before reinstall also boot with liveCD and backup your files.

And an other (dirty) way, reinstall without formatting

---

### Post by Robing Goodfellow on 2011-04-01
```

ubuntu@ubuntu:~$ sudo mount --bind /dev /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7
ubuntu@ubuntu:~$ sudo mount --bind /proc /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7
ubuntu@ubuntu:~$ sudo mount --bind /sys /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7
ubuntu@ubuntu:~$ sudo chroot /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7
chroot: failed to run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

---

### Post by Phil D. on 2011-04-01
you forgot the /dev,/proc and /sys at the end of the mount lines

---

### Post by Robing Goodfellow on 2011-04-01
I'm missing something ridiculously simple, but can't see it:

```

ubuntu@ubuntu:~$ sudo mount --bind /dev /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7/proc
mount: mount point /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7/proc does not exist
ubuntu@ubuntu:~$ sudo mount --bind /sys /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7/sys
mount: mount point /media/d70e6f6d-c54e-46cf-b34f-9cd1947b44c7/sys does not exist



```

---

### Post by cbowman57 on 2011-04-01
This de-mystifies things if you have the ability to download & burn the iso to CD or USB.  

Rescatux
[http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/]("http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/")

---

### Post by Robing Goodfellow on 2011-04-01
@ Chuck, thanks, I'll have to try it when I get home.  The internet connection here is spotty at best and slow always.

@Phil, tried it, not sure what I did wrong but when I get to the proc and sys entries (as shown in post above) it tells me the system is not mounted there, though a quick check showed it was.

I've come to the point where I'm more concerned about recovering one file than the system.  Any ideas how to get into a LibreOffice Calc file without permission?

regards, Richard

---

### Post by grahammechanical on 2011-04-01
May I make a suggestion or two. Copy that file and any others that you want to another partition on the hard disc. It would be nice if you could copy the file off the hard disc but as you will using the CD drive with the Live CD I guess that is not possible.

Once you have reinstalled and got Ubuntu loading, then copy the file back over to the documents folder and see if LibreOffice will open it. Otherwise, load up the Nautilus file manager and browse to the file. Right click on it and select Permissions and see if you can make the file read & write. All you need is to Read permission then you can copy the data into a new spreadsheet.

Is this file in the partition where Maverick is? Then install Maverick again in the first partition. It will give you access to the file which you can copy to CD. Then install Natty over the second Maverick install. I had to do something like this when I messed up my system and need to save my data.

Regards.

I wish you better.

---

### Post by Robing Goodfellow on 2011-04-01
I just installed Natty over Maverick and it repaired the Grub and also gave me back all of my files.  Backing everything up now.  Not sure I like Natty as much as I did Maverick, seems a bit more difficult to find stuff and get things done, though I'm willing to believe, for the weekend anyway, that this is because I was used to Maverick.  Worst case scenario, now that I have my files and am backing them up, I can format the entire drive and put Maverick back on.

Thanks for all the assistance folks.  I do love this community!

regards, Richard

---

