---
title: "Partition rescue after hibernate"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Ansatsu on 2011-04-19
My netbook (thinkpad x100e with Ubuntu 10.10 Netbook Edition) crashed  after it went into hibernate mode so i had to force a reboot.

Since then I get into grub menu during the boot (which I was never before) and after booting a kernel image, it shows a command line like:
```

(initramfs) _

```I tried to boot a LiveUSB Ubuntu and mount the partition, but it alway says
```

mount: mounting /dev/sda1 on /mnt/sda1/ failed: Device or resource busy

```I also checked the disk, no errors.

partition layout (default)
```

/dev/sda1   linux (ext4)
/dev/sda2   extended
/dev/sda5   swap

```any help? :/

---

### Post by Paddy Landau on 2011-04-19
I'm not entirely sure if this will work, but maybe if you check the disk.

Boot from a Live CD. Do not mount the disk. Open a terminal and enter:
```
sudo fsck -MC /dev/sda1
```
You might have to force the check:
```
sudo fsck -MCf /dev/sda1
```

---

### Post by Ansatsu on 2011-04-20
thanks for your reply

```

root@ubuntu:/home/ubuntu#fsck -MCf /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1

```In the meantime I managed to access the partition over grub command-line.
Is there a way to copy data with grub to a usb drive?

---

### Post by psusi on 2011-04-20
> **Ansatsu said:**
> fsck.ext4: Device or resource busy while trying to open /dev/sda1
[/CODE]In the meantime I managed to access the partition over grub command-line.
Is there a way to copy data with grub to a usb drive?

No, grub can't write to disks.  Are you sure sda is the hard disk and not a usb flash stick you are booting from?  If so, then you must have mounted the drive already ( places menu? ) so you need to unmount it.

---

### Post by Paddy Landau on 2011-04-21
Boot from the Live CD. Ensure you do *not* select anything in Places; just open a terminal.

In the terminal, enter the command:
```
sudo parted --list
```Post the results here.

---

### Post by Ansatsu on 2011-04-21
> Post the results here.     ```

root@ubuntu:/home/ubuntu# parted --list
Model: ATA STT_FTM32GX25H (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  30.7GB  30.6GB  primary   ext4            boot
 2      30.7GB  32.0GB  1364MB  extended
 5      30.7GB  32.0GB  1364MB  logical   linux-swap(v1)


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot



```> 
No, grub can't write to disks.  Are you sure sda is the hard disk and   not a usb flash stick you are booting from?  If so, then you must have   mounted the drive already ( places menu? ) so you need to unmount it.   
As shown above: sda is my SSD and sdb is the usb stick. sda1 is not mounted, but each try results in 'device is busy'

---

### Post by Paddy Landau on 2011-04-21
Thanks for the data.

OK, somehow your ext4 disk has been marked as in-use. Something went wrong there.

Again from a Live CD, do the following in a terminal.
```
mount
```This will show you what is mounted. Check for any occurrence of sda1.

If you **do** see sda1:
```
sudo umount /dev/sda1
```Then try this command. Note the changes to the parameters.
```
sudo fsck -Cfp /dev/sda1
```

---

### Post by oklokl on 2011-04-21
boot cd
sudo -i

fdisk -l
fsck.ext4[COLOR=#FF0000] -p[/COLOR] [COLOR=#0900FF]/dev/sda1[/COLOR]
fsck.ext4 [COLOR=#FF0000]-c [/COLOR][COLOR=#0900FF]/dev/sda1

[/COLOR] -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list


ntfs&#51032; &#44221;&#50864;

sudo ntfsfix /dev/sda1

or 
**fsck.ext4 -a [COLOR=#FF0000]/dev/sda1[/COLOR]**
[B]fsck.ext4 -c [COLOR=#FF0000]/dev/sda1

[/COLOR][/B]HDD Regenerator ->iso boot ->repair
Bad Sector

---

### Post by Ansatsu on 2011-04-21
sda1 is not listed in 'mount' and fsck shows the same error.
I even tried it with a Gentoo LiveCD.

Something is wrong with sda1:
```

livecd# cfdisk /dev/sda
FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder

```but with grub I can still access all data (ls/cat)

---

### Post by Paddy Landau on 2011-04-21
Ansatsu, I'm sorry, I have hit the limits of my knowledge here.

From the Live CD, you can go to System > Administration > GParted and see whether you can check the disk from there (though I doubt you'll get any further).

Also try System > Adminstration > Disk Utility. Try to check the file system, and check the SMART Data (if there is any).

I hope someone else with more knowledge can help you.

---

### Post by Ansatsu on 2011-04-21
yeah i finaly got it! :D

so here's the solution:

first I made an image of the whole disk (with a LiveCD)
```

ddrescue /dev/sda /mnt/usb/rescue.img

```then mapped the whole image on another pc as drive
```

# losetup /dev/loop0 /mnt/usb/rescue.img 
# fdisk -l /dev/loop0 

Disk /dev/loop0: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d126

      Device Boot      Start         End      Blocks   Id  System
/dev/loop0p1   *        2048    59865087    29931520   83  Linux
/dev/loop0p2        59867134    62531583     1332225    5  Extended
/dev/loop0p5        59867136    62531583     1332224   82  Linux swap / Solaris

```partion 1 has an offset of 512 x 2048 = 1048576 bytes (sector size * partition start)
so I could remount only the first partition
```

losetup -d /dev/loop0
losetup -o 1048576 /dev/loop0 /mnt/usb/rescue.img

```now I run e2fsck, which fixed all errors
```

e2fsck /dev/loop0

```and finaly mounting the filesystem
```

mount /dev/loop /mnt/rescue

```clean up, afterwards
```

umount /mnt/rescue
losetup -d /dev/loop0

```

---

### Post by Paddy Landau on 2011-04-22
Wow. I would not have managed to figure that out. Well done.

What will you do now -- back up, reformat and restore?

---

### Post by Ansatsu on 2011-04-22
I could try to write the rescued image back to the drive, but I think its safer to reinstall the system ;)

---

