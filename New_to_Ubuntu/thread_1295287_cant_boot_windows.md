---
title: "cant boot windows"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by patchido on 2009-10-19
i had windows installed, but when i installed ubuntu 9.04 i had to place manually the partitions and the menu.lst was missing windows, i tried making it but it wont work, it just stays as loading(grub) and wont start windows, this is my fdisk

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65cc02ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         637     5108670    5  Extended
/dev/sda2   *         638        1274     5116702+  83  Linux
/dev/sda3            1275        1523     2000092+  82  Linux swap / Solaris
/dev/sda5               2         637     5108638+   7  HPFS/NTFS

```


and this my menu.lst

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Guindows Xp
root		(hd0,4)
savedefault
chainloader	+1
```

---

### Post by rccn on 2009-10-19
You might want to try

```
sudo update-grub
```It will check your partitions for installed kernels and then alter menu.lst accordingly.

---

### Post by DGortze380 on 2009-10-19
Is your windows install on a primary partition?

EDIT:

Nevermind. You have to add your Windows install to menu.lst.
For your install root for windows should be (hd0,4).
There is in example in the file, should look something like this:

```

title         Windows 7 Professional
root          (hd0,1)
makeactive
chainloader   +1

```

---

### Post by patchido on 2009-10-19
> **DGortze380 said:**
> Is your windows install on a primary partition?

EDIT:

Nevermind. You have to add your Windows install to menu.lst.
For your install root for windows should be (hd0,4).
There is in example in the file, should look something like this:

```
[CODE]
```
title         Windows 7 Professional
root          (hd0,1)
makeactive
chainloader   +1
[/CODE]




well, i tried that, and it got error, invalid input device, or something like that,



this is my new menu.lst

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/memtest86+.bin
quiet

title         Guindows xp
root          (hd0,4)
makeactive
chainloader   +1
```

---

### Post by Mark Phelps on 2009-10-19
Looks like you may have wiped out MS Windows in the process of installing Ubuntu.  Look at your fdisk results.  The "extended" partition in sda1 has the same addresses as your MS Windows partition.

I would boot into Ubuntu, go to Places, and open the folder for your MS Windows partition to confirm that the files are still there.

---

### Post by e_james on 2009-10-19
In my experience, for minimum complications, Windows XP should be installed in the first primary partition in the partition table. This is where it would normally be if it was the sole OS. I am inclined to agree with Mark Phelps diagnosis. Windows appears to be in a logical partition (sda5) within an extended partition (sda1). I would not expect this to work.

---

### Post by patchido on 2009-10-19
so what i understand ive got to do is this, i have to get into live cd and delete all the partitions, format it and then install windows over it, and with the ubuntu installation ill reduce the size of windows and after ive done that i can do the 3rd partition from parition editor??


my only question is the next, what format should i use for my data partition?? where there is no OS, i want to be able to save everything in there, i want to leave untouched the OS partitions

---

### Post by DGortze380 on 2009-10-19
> **patchido said:**
> 
my only question is the next, what format should i use for my data partition?? Where there is no os, i want to be able to save everything in there, i want to leave untouched the os partitions

ntfs

---

### Post by patchido on 2009-10-19
any reasoning on why ntfs?? i know it is accesible for the two systems, but is it better?

---

### Post by e_james on 2009-10-19
Starting with an empty drive, my personal strategy is to create the first partition (primary, sda1) as NTFS for Windows XP somewhere between 15GB and 30GB. The larger size is needed for Windows extras such as Google desktop search which tend to put GB data files on the C drive. Linux doesn't need a primary partition but the boot partition (or / if there is no /boot) can't be too far away from the start of the drive. There is a specific figure which I have forgotten but I think you can get away with at least 80GB space from the start. Depending on what I have in mind for the PC I might create a second primary partition for /boot (about 100MB or for / (about 10GB). At this time I would be cautious about ext4 but ext 2 or ext 3 would be fine. The rest of the space can go in an extended partition as logical partitions. one for Windows data (NTFS or FAT32), one for /home and one for swap. If you plan to use hibernation, the swap partition has to be at least as big as the ram. Windows needs a similar amount of space on the C drive for the hyberfil. You should take note that, if Windows does not shut down cleanly (i.e. crashes), then any NTFS partitions will probably be inaccessible from linux. I often create a FAT32 partion of about 30GB specifically to facilitate backup operations such as partition images. If you normally use the "My Documents" folder for data files then you should consider applying the option to move it to a drive other than the C drive. This is roughly the equivalent of the linux /home partition.

---

### Post by Incendia on 2009-10-19
> **patchido said:**
> any reasoning on why ntfs?? i know it is accesible for the two systems, but is it better?

Windows only works well on NTFS. You can use FAT32; but there are performance/technical complications and whatnot.

---

### Post by DGortze380 on 2009-10-19
> **DGortze380 said:**
> ntfs

NTFS Support in Linux (ntfs-3g) is very good (especially if you have a Windows Install to fix occasion 'unclean' drive issues.

Windows almost requires NTFS at this point... as stated, you can use FAT32 but there are file size limitations, and in my experience it corrupts, OFTEN.

Simply stated, NTFS has the best combination of support in both OSes.

---

### Post by oldfred on 2009-10-19
I created my shared data partition about 3 years ago as FAT32 because the NTFS driver back then was still not quite up to snuff (it is fine now). But I decided to put my backups on the Fat partition and they were always about 4GB which I assumed was ok. When I recently switched to running my backups to an ext3 partition it was 3 times larger. Bottom line do not use FAT for anything that will have large files as you will not have a complete copy.

---

### Post by Mark Phelps on 2009-10-19
In terms of Windows OSs, XP CAN work with FAT32, but all MS Windows OSs since then (and even newer Service Packs of XP) require NTFS.

Plus, with the NTFS-3G package, native Linux support for NTFS file systems is quite good.

Finally, you won't be hampered with the filesize limitations of FAT32 if you use NTFS.

---

### Post by LewRockwell on 2009-10-19
definitely ntfs

.

---

