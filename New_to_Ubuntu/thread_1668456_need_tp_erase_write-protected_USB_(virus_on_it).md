---
title: "need tp erase write-protected USB (virus on it)"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Red Raven on 2011-01-16
i have a USB pin drive with a virus on it. the virus is nortel, which i believe is a windows based virus so i should be good. but the virus has write-protected the whole USB so you can't delete it. i've tried Gparted (formatted and erasing), and even used a dd command. the dd seemed to work, but then i checked in nautilus and all the file were still there. i don't care about the stuff on it. can anyone help me?

---

### Post by sandyd on 2011-01-16
> **Red Raven said:**
> i have a USB pin drive with a virus on it. the virus is nortel, which i believe is a windows based virus so i should be good. but the virus has write-protected the whole USB so you can't delete it. i've tried Gparted (formatted and erasing), and even used a dd command. the dd seemed to work, but then i checked in nautilus and all the file were still there. i don't care about the stuff on it. can anyone help me?
post output of
```

sudo fdisk -l
```

---

### Post by kn0w-b1nary on 2011-01-16
how about installing bleachbit:
sudo apt-get install bleachbit
sudo bleachbit

And then when the window opens, click
file
shred folder

and select USB

Hope this helps!

---

### Post by Red Raven on 2011-01-16
> **sandyd said:**
> post output of
```

sudo fdisk -l
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79120785

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26611   213545984    7  HPFS/NTFS
/dev/sda3           30389       30402      105656    c  W95 FAT32 (LBA)
/dev/sda4           26611       30388    30339073    5  Extended
/dev/sda5           26742       30388    29291520   83  Linux
/dev/sda6           26611       26742     1047552   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8021 MB, 8021606400 bytes
16 heads, 32 sectors/track, 30600 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       30600     7829568    c  W95 FAT32 (LBA)

---

### Post by sandyd on 2011-01-16
> **Red Raven said:**
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79120785

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26611   213545984    7  HPFS/NTFS
/dev/sda3           30389       30402      105656    c  W95 FAT32 (LBA)
/dev/sda4           26611       30388    30339073    5  Extended
/dev/sda5           26742       30388    29291520   83  Linux
/dev/sda6           26611       26742     1047552   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8021 MB, 8021606400 bytes
16 heads, 32 sectors/track, 30600 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       30600     7829568    c  W95 FAT32 (LBA)
```

dd if=/dev/random of=/dev/sdb bs=1M

```

---

### Post by Red Raven on 2011-01-16
> **sandyd said:**
> ```

dd if=/dev/random of=/dev/sdb bs=1M

```
i told you i tried the dd command.

---

### Post by Red Raven on 2011-01-17
anyone? I really need this drive to work. I'd hate to throw out 8GB worth of free space. (whatI really mean is i don't want to buy a anew one.)

---

### Post by CharlesA on 2011-01-17
What makes you think that there is a virus on your USB?

What files are there after you formatted the drive?

---

### Post by CharlesA on 2011-01-17
What makes you think that there is a virus on your USB?

What files are there after you formatted the drive?

---

### Post by Red Raven on 2011-01-17
> **CharlesA said:**
> What makes you think that there is a virus on your USB?

What files are there after you formatted the drive?
its very possible that there is not one, but in that case its has some extremely powerful write protection (or im just missing something). how ever it got that protection after being exposed to a computer with the virus if i remember correctly. however there are no suspicious files. only the 4 that should be there: 2 music folders, on folder with some Docs in it, and one .exe for a program i tried putting on it (the .exe is NOT the virus. i put it on there).

---

### Post by psusi on 2011-01-17
You need to dd it when it is NOT mounted.

And you don't use /dev/random.  That will block until there is enough entropy for good random data, so it will take eons.  If you must use random data use /dev/urandom.

---

### Post by fatality_uk on 2011-01-17
> **Red Raven said:**
> its very possible that there is not one, but in that case its has some extremely powerful write protection (or im just missing something). how ever it got that protection after being exposed to a computer with the virus if i remember correctly. however there are no suspicious files. only the 4 that should be there: 2 music folders, on folder with some Docs in it, and one .exe for a program i tried putting on it (the .exe is NOT the virus. i put it on there).

Perhaps I am missing something! Are you saying that once you run DD that the 4 files you describe above are still there?

---

### Post by JC Cheloven on 2011-01-17
Hi Red,

A virus simply can't do that you're reporting. Please:

In gparted, choose the pendrive in the droplist (at the up-right corner).
Go to the "device" menu, and choose "create new partition table".
When finished, create a new filesystem. Probably you'll want fat32 (my suggestion).

If the above doesn't work, I'm affraid your pendrive is screwed itself. Nothing to do with an OS or a virus.

---

### Post by corrytonapple on 2011-01-17
> **JC Cheloven said:**
> 
If the above doesn't work, I'm affraid your pendrive is screwed itself. Nothing to do with an OS or a virus.
Don't say that yet!  If anyone here has an 8GB USB drive that they can make an Image of, than there may be a hope.  Now it does use DD, but DD is used for putting the image on the drive.  Now, I only have a 4GB Flash drive, but if someone here has a _**Blank, 8GB, Working USB Drive,**_ and they can make an image of it using DD, then post it up somewhere on the web where the OP can get it, then put it on his flash drive, then it might work.  To make an image of your Flash Drive run this in the Terminal:
```

dd if=/dev/sdb of=/path/to/image.img

```
The "if=/dev/sdb" is your path to the flash drive, and the "of=/path/to/image.img" is the path to where you want your .img (Or Image) to be stored.  That I know of, it must have the .img extension.  Once that image has been made and posted on the web where the OP can get it, the OP needs to download it to his HDD (Hard Drive) and run the following command:
```

dd if=/path/to/image.img of=/dev/sdb

```
Again, the "if" is the path to where the image is stored on your HDD, and the "of" is the path to your flash drive.  I have not done this in a while, so tell me how it looks.  Just my two cents.....

---

### Post by psusi on 2011-01-17
> **corrytonapple said:**
> Don't say that yet!  If anyone here has an 8GB USB drive that they can make an Image of, than there may be a hope.  Now it does use DD, but DD is used for putting the image on the drive.  Now, I only have a 4GB Flash drive, but if someone here has a _**Blank, 8GB, Working USB Drive,**_ and they can make an image of it using DD, then post it up somewhere on the web where the OP can get it, then put it on his flash drive, then it might work.  To make an image of your Flash Drive run this in the Terminal:


The goal here is to erase the stick, not replace its contents with those of another one.

Again, when you dd, it must NOT be mounted, or the mount will still remember the old contents and/or become completely screwed up.

---

### Post by corrytonapple on 2011-01-17
> **psusi said:**
> The goal here is to erase the stick, not replace its contents with those of another one.

Again, when you dd, it must NOT be mounted, or the mount will still remember the old contents and/or become completely screwed up.
Well I believe that the only way to do this is by erasing it.  Unless someone can come up with another way.  Anyway, the only contents you are replacing at most would be the format, such as FAT 32 or NTFS.  It may not be a virus, but I did this very thing with a friend and a Read Only Flash Drive (Which I still do not know how that happened) and it worked.  Why not here?
Yes, the Flash Drive MUST NOT be mounted.

---

### Post by psusi on 2011-01-17
> **corrytonapple said:**
> It may not be a virus, but I did this very thing with a friend and a Read Only Flash Drive (Which I still do not know how that happened) and it worked.

If you were able to write to it, then by definition, it was not read only ;)

---

### Post by Red Raven on 2011-01-17
sorry to keep posting, but i really need help.

---

### Post by psusi on 2011-01-17
> **Red Raven said:**
> sorry to keep posting, but i really need help.

Well, did you try to dd zeros over the drive *without it mounted* or not?

---

### Post by Red Raven on 2011-01-17
wow sorry. for some reason my pc didn't load all the new answers. give me a sec to read them all.

---

### Post by Red Raven on 2011-01-17
I can't mount it, its grayed out. yes, i treid DD, but it was all still there. same thing with new partition table.

---

### Post by wilee-nilee on 2011-01-17
> **Red Raven said:**
> I can't mount it, its grayed out. yes, i treid DD, but it was all still there. same thing with new partition table.

Open the menu-system-admin-disc utility

Does it show it as mounted or unmounted? It will say mount or unmount what does it say?

---

### Post by Red Raven on 2011-01-17
> **wilee-nilee said:**
> Open the menu-system-admin-disc utility

Does it show it as mounted or unmounted? It will say mount or unmount what does it say? I'll try it this afternoon when I get home. Thx!

---

### Post by corrytonapple on 2011-01-17
> **psusi said:**
> If you were able to write to it, then by definition, it was not read only ;)
I know, I know.  But that is what happened.  Really a miracle....
Best of luck to the OP.  I cannot think of anything more to do.

---

### Post by Red Raven on 2011-01-17
tried it without mounting. it was already unmounted when i plugged it in. but it still didn't work.

---

### Post by JC Cheloven on 2011-01-18
So the "create partition table" bit didn't help... I don't have much hope then (as I said; I wish I'd be wrong), but let's see if this gives us further tips:

- Shutdown the system. Do a fresh reboot.

- With nothing plugged at usb (nor the pendrive), run those:
```
mount -l
ls /media
ls /dev |grep sd
```

- Now plug in the pendrive. Wait for a while and repeat the above commands:
```
mount -l
ls /media
ls /dev |grep sd
```

Hopefully this will give a clue, at least, about the mounting status of the device when plugged.

---

### Post by Red Raven on 2011-01-18
> **JC Cheloven said:**
> So the "create partition table" bit didn't help... I don't have much hope then (as I said; I wish I'd be wrong), but let's see if this gives us further tips:

- Shutdown the system. Do a fresh reboot.

- With nothing plugged at usb (nor the pendrive), run those:
```
mount -l
ls /media
ls /dev |grep sd
```- Now plug in the pendrive. Wait for a while and repeat the above commands:
```
mount -l
ls /media
ls /dev |grep sd
```Hopefully this will give a clue, at least, about the mounting status of the device when plugged.
first output: 

```
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ mount -l
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/red-raven/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=red-raven)
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ ls /media
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ ls /dev |grep sd
```

second output:

```
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ mount -l
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/red-raven/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=red-raven)
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ ls /media
red-raven@redraven-Presario-CQ62-Notebook-PC:/$ ls /dev |grep sd
```

---

### Post by JC Cheloven on 2011-01-18
Well, identical outputs in both cases. It's clear that your pendrive is not being mounted at all. It should, under normal conditions, of course. 

I guess that after plugging it, the command
```
sudo fdisk -l
``` does not recognise the device either (?). If it does, it would show a line starting by /dev/sdb1, or at least /dev/sdb. If you find such a line, perhaps we can try a manual mounting, and see further.

---

### Post by JC Cheloven on 2011-01-24
@RedRaven: 
Hey, after 6 days... how this ended up? My former bet of the pendrive being faulty, was it finally right? Or you succeded at some point?

---

### Post by chernobyl on 2011-08-11
I've been hitting a very similar issue with 2 USB flash ("pen") drives.  Already threw one out, and now the replacement is showing the same symptoms.  Here's the lowdown:
I was originally operating on these drives under Windows and finally got fed up with their horrible interpretation of 'user-friendly' so I took the pen drive home to muck it up with Linux.  The drive was already "partially" flashed (i.e. no partition table) due to my Windows goofiness, but now the thing just won't write.  Everything I do reports some form of a write-protect error: and no, there is not a switch.

"sudo fdisk -l" reports:
```
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

after inserting pen drive, dmesg says:
```
[279582.416036] usb 1-5: new high speed USB device using ehci_hcd and address 11
[279582.671385] scsi11 : usb-storage 1-5:1.0
[279583.668793] scsi 11:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 2
[279583.671519] sd 11:0:0:0: Attached scsi generic sg2 type 0
[279583.672517] sd 11:0:0:0: [sdb] 32929792 512-byte logical blocks: (16.8 GB/15.7 GiB)
[279583.673665] sd 11:0:0:0: [sdb] Write Protect is off
[279583.673670] sd 11:0:0:0: [sdb] Mode Sense: 03 00 00 00
[279583.673674] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[279583.676034] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[279583.916804]  sdb: unknown partition table
[279583.918260] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[279583.918264] sd 11:0:0:0: [sdb] Attached SCSI removable disk

```
So then I do what makes sense, "sudo fdisk /dev/sdb", and press n, p, 1, enter, enter, t, b, w, enter (new partition, whole drive, FAT32, write) and get:
```
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.

Error closing file

```
Now dmesg reads:
```
[280025.090549] sd 11:0:0:0: [sdb] Device not ready
[280025.090553] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[280025.090557] sd 11:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[280025.090562] Info fld=0x0
[280025.090564] sd 11:0:0:0: [sdb]  <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[280025.090570] sd 11:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 00 00 00 08 00
[280025.090579] end_request: I/O error, dev sdb, sector 0
[280025.090582] Buffer I/O error on device sdb, logical block 0
[280025.090584] lost page write due to I/O error on sdb
[280025.429949] sd 11:0:0:0: [sdb] Write Protect is on
[280025.429954] sd 11:0:0:0: [sdb] Mode Sense: 03 00 80 00
[280025.429957] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[280025.432967]  sdb: unknown partition table

```
I've tried squashing the MBR ("dd if=/dev/zero of=/dev/sdb bs=512 count=1") which reports success but drops a write protect error into dmesg.
Is it really fried? It's brand-new, and replaces another identical drive that had identical issues.
Note: After any attempts to write to the drive, I must remove and re-insert the drive, as the system will recognize it as write-protected and refuse to perform operations.
HALP!  Or hit me with a herring until I'm unconscious.

---

