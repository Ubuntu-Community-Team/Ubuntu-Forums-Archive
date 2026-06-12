---
title: "External FAT 32 Hard drive on 9.04 NOT READING or WRITING"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by sonny123 on 2009-10-20
Brand new to linux, average user of windows & DOS
have installed ubuntu okay on a Pentium 4, 3Ghz with 256 RAM,  
my USB pen drive works but cannot get Usb ext hard drive to work. have read a few post already but cant resolve the issue 
 
The drive was NTFS, backed up data to another laptop running Vista home premium,  Created the FAT 32 partition with gParted. and it all seemed to work okay,
plugged the drive back into other laptop copied all my files back to it.

When i plugged drive back into ubuntu laptop, I can see the drive in the GUI file browser, (I did browse into the root of the drive once but couldnt write to it.) 
The Icon appears on the desktop and in places menu. but i cannot read or browse it.
I plugged back into windows and that will now not read the drive either
If i open up gparted it just scans continuously but finds no drives at all not even the internal drive  

this is what i get from sudo fdisk-l.  when i put it into terminal the cursor continues to blink and if i try to close terminal it says "There is still a process running in this terminal. Closing the terminal will kill it"

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0c5216f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4785    38435481   83  Linux
/dev/sda2            4786        4864      634567+   5  Extended
/dev/sda5            4786        4864      634536   82  Linux swap / Solari

anybody any ideas or walk me through what to try next  :confused:
Thanks in advance

---

### Post by oldfred on 2009-10-20
When I had three drives 2 sata and 1 pata it took 45 minutes for gparted to complete its scan. With only 256MB of memory and an external it may take a while.

Fat can be fragile, NTFS is better.
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

I would try a filecheck first:

Must be unmounted
sudo dosfsck -a <the fat32 device>

 or

You might need dosfstools and ntfsprogs as well.
sudo /sbin/fsck.vfat -V <the fat32 device>

---

### Post by sonny123 on 2009-10-20
Thanks fred,
I didnt think i could use NTFS and read & Write with ubuntu,
When I created the FAT 32 partition GParted scanned it in seconds,
The confusing part is that windows ( on other machine) will not now read the drive either, where as it read & wrote to it perfectly when i restored the files to the FAT32  created with Gparted.

when i created the FAT 32 partition i could have sworn i called it "160G" but in the file browser it names it "160.0 GB media"

sudo dosfsck -a <the fat32 device>  does this do a file check or unmount the drive, I can't unmount the drive from the Browser

sudo /sbin/fsck.vfat -V <the fat32 device>  What does this do?

---

### Post by sonny123 on 2009-10-20
when trying to unmount from the browser i get 
Error org.freedesktop.Hal.Device.InterfaceLocked.
 have had gparted scanning for over 30 mins but cxannot detect any drives

---

### Post by oldfred on 2009-10-20
When I was checking on linux filecheck programs I found both --help showed they seemed to be the same. I just ran both and the second seems slightly more complete. On my machine neither did anything, the /sbin/fsck.vfat showed some lines showing progress was the only difference. To unmount use the umount (no n) command. On my machine it said it was not mounted since it is a drive I do not always mount.

If filecheck does not work then testdisk is the next level of partition checking. It is in the repositories so you can download it and it is on most liveCDs.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

