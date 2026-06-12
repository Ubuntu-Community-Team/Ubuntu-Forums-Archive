---
title: "Lost XP for good haven't I"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by John Hale on 2009-01-08
Was trying to do a dual boot version as windows was throwing up more and more error messages, during the partitioning an error message came up and had a recommended thing to click this repartitioned my hole hard drive so I'm guessing theres no way back.

Also I'd like to put windows back on and use ubuntu for the web and emails, but I only have the xp upgrade disc and with no windows on here i can't reinstall

HELP

John

---

### Post by hyper_ch on 2009-01-08
there still might be a hidden partition that contain the original image of your system. Post the output of:

```

sudo fdisk -l

```

---

### Post by 73ckn797 on 2009-01-08
> **John Hale said:**
> Was trying to do a dual boot version as windows was throwing up more and more error messages, during the partitioning an error message came up and had a recommended thing to click this repartitioned my hole hard drive so I'm guessing theres no way back.

Also I'd like to put windows back on and use ubuntu for the web and emails, but I only have the xp upgrade disc and with no windows on here i can't reinstall

HELP

John

If you truly have lost Windows and only have the upgrade disk, I assume you know, that if you have a previous upgrade or full Windows 98 disk you can still install Windows.

I would install Windows first then resize disk and partition free space for Ubuntu.

---

### Post by javahollic on 2009-01-08
All is not lost, the data will be there still, the Partition table can be spliced any which way and recovered in the following way, **so long as you havent formatted the disk :(**

For this act of wizardry you will need:
1. a bootable Ubuntu CD, no way around it
2. a Usb key
3. a working windows system with a similar boot structure (failing this, go to : [how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

Step1: restore the partition structure on your windows box:
1. boot from the Ubuntu CD, get to a prompt
2. use fdisk to remove all partions set on the disk, eg 'fdisk /dev/sda', 'd 1' to remove part1 etc.
3. again with fdisk, recreate the one and only partition, set the partition type to NTFS, save the changes.

Step2: nick a windows MBR from a working box
1. boot the working windows box off the Ubuntu cd, get to a prompt
2. plugin the usb key, assuming it now resides at /dev/sdb, mount it somewhere with 'mkdir /media/usb ; mount /dev/sdb1 /media/usb'
3. execute 'dd if=/dev/sda of=/media/usb/doze.mbr bs=436 count=1'
4. execute 'sync' to ensure changes are committed to the key
5. execute 'umount /media/usb'
6. remove the key, shutdown the box.

Step 3. Restore the MBR on the bust box (if it doesnt 'boot')
1. boot the working windows box off the Ubuntu cd, get to a prompt
2. plugin the usb key, assuming it now resides at /dev/sdb, mount it somewhere with 'mkdir /media/usb ; mount /dev/sdb1 /media/usb'
3. execute 'dd if=/media/usb/doze.mbr of=/dev/sda bs=436 count=1'
4. rebooting should enable the disk to be bootable, and your recovered partition usable.

Suggest next time you do this get a usb portable drive and backup the ENTIRE disk with:

dd if=/dev/sda of=/media/usb/mybackup.dd bs=512

If you screw up, a restore is then trivial: dd if=/media/usb/mybackup.dd of=/dev/sda bs=512

You probably also want to use ntfresize to resize your Doze partition _before_ installing Ubuntu, that, or get another disk...

ttfn ;)

---

### Post by bumanie on 2009-01-08
You could try testdisk - it is a partition and data retrieval program. There is also ntfsprogs which includes ntfsundelete, as you can see it can (under the right conditions) undelete an accidentally deleted ntfs filesystem. Testdisk can be obtained from [here]("http://www.cgsecurity.org/wiki/TestDisk") as a live cd or can be installed in ubuntu via code > sudo apt-get install testdiskand then started in terminal with code > sudo testdiskHere a link to [ntfsprogs]("http://man.linux-ntfs.org/ntfsprogs.8.html")To install in ubuntu > sudo apt-get install ntfsprogs

---

### Post by John Hale on 2009-01-08
I maybe a thickie, but I didn't intend to be a dropped in a the deep end I've gone into Synaptic Package Manager and installed Testdisk, where do I find or how do I create the icon and run the thing I getting frustrated it's like trying to learn a new language

---

### Post by tangibleorange on 2009-01-08
don't worry - it can all be a bit daunting at first!

firstly, try going to a terminal (Applications -> Accesories -> Terminal) and typing:
```
sudo fdisk -l
```

then paste the output here. that will tell us what partitions are on your system. if necessary, we can then run testdisk

---

### Post by John Hale on 2009-01-08
Here it is:

john@john-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03f360b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         556     4466038+  83  Linux
/dev/sda2             557        9729    73682122+   5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda6             557        9353    70661839+  83  Linux
/dev/sda7            9354        9541     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3228 MB, 3228696576 bytes
255 heads, 63 sectors/track, 392 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d353d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         368     2955928+  83  Linux
/dev/sdb2             369         392      192780    5  Extended
/dev/sdb5             369         392      192748+  82  Linux swap / Solaris
john@john-desktop:~$ 

can't see any ntfs or whatever so I assume it's a done deal

---

### Post by tangibleorange on 2009-01-08
hmm im afraid that doesnt look good.... i can't see any NTFS :(. i think windows is gone.

---

