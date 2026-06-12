---
title: "Someone kindly check my external HD setup?"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by paker on 2011-06-11
I am using 2 internal hard drives with a dual usb/e-sata docking station, usb connected, to store video and audio files. They get connected to PC a few times a month.

Docking station
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153112&cm_re=thermaltake_hard_drive_dock-_-17-153-112-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153112&cm_re=thermaltake_hard_drive_dock-_-17-153-112-_-Product)

According to Disk Utility,

DRIVE
Samsung HD154UI
Device: /dev/sdc
Connection: USB at 480.0 MB/S
Partitioning: Master Boot Record
SMART status: unknown

VOLUME
Device: /dev/sdc1
Partition Type: HPFS/NTFS (0x07)
Type: NTFS
Labele: (blank)

DRIVE
WDC WD20EARS
Device: /dev/sdb
Connection: USB at 480.0 MB/s
Partitioning: Master Boot Record
SMART Status: Disk is healthy

VOLUMES:
Device: /dev/sdb1
Partition Type: HPFS/NTFS(0x07)
Partition Flags: Bootable
Type: NTFS
Label: Shelf1

1) Is there a reason to make an external hard drive bootable?
2) What is Master Boot Record partitioning? I wonder if I made a mistake when I installed the HD first time.
3) How do I change label?
4) Should I start using e-sata connection? I have an e-sata on PC backpanel.
5) Is it true that the Wester Digital 4 kb sector hd needs a special formating? 
6) Why don't I see "SMART Status: Disk is healthy" in Samsung 1.5 TB?

Thanks.

10.04 LTS

---

### Post by VOT Productions on 2011-06-11
1) Only if you have an OS installed on it.
2) MBR is the small sector of the Hard Drive were you hold GRUB info, etc. Don't worry about it.
3) [Ubuntu Help Article]("https://help.ubuntu.com/community/RenameUSBDrive")
4) E-Sata is way faster, but you have to enable it in BIOS.
5) It's recommended you use 4KB sectors with WD Advanced Format drives **only.** "With the emulation of 512B sectors, there&#8217;s the risk that a partition could be misaligned compared to the 4K physical sectors - where it would be unwittingly started in the middle of such a sector. As a result, the clusters of a file system on that partition would end up straddling 4K sectors, which would cause performance problems. "
6) Not sure, but if it works fine, leave it alone.

---

### Post by Rocket2DMn on 2011-06-11
1. No, not unless you are running Grub from there.
2. Not really sure, maybe it means the MBR is able to access it? I wouldn't worry about this.
3. You should be able to re-label drives when they are unmounted using Disk Utility (click Edit Filesystem Label). Other options include GParted, or manually at the command line, see [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
4. I haven't used this, but if your external supports it you might see a speed improvement.
5. I haven't heard this before, are you having trouble reading the drive?
6. SMART status doesn't show on external USB hard drives. It may work with eSata though (again I haven't used it).

---

### Post by fabricator4 on 2011-06-11
> **paker said:**
> 
1) Is there a reason to make an external hard drive bootable?

Yes, so that you can boot off it.  :-)

Don't worry about it, it's just that the primary partition has the boot flag set, which is normal.  It won't affect you at all.

> 2) What is Master Boot Record partitioning? I wonder if I made a mistake when I installed the HD first time.


The master boot record (MBR) is a set of instructions for loading the operating system, what files to load where, in essence.  It can also be more complex, such as grub which allows you to select operating systems and kernels at boot time.  Don't worry about it: it's reserved space and has no bearing on what is a purely data only drive.

> 3) How do I change label?

Use Disk Utility.  The drive must not be mounted to be able to change the volume label, but you can unmount the drive in Disk Utility as well.


> 4) Should I start using e-sata connection? I have an e-sata on PC backpanel.

It would be faster to do so, but it's up to you.

> 5) Is it true that the Wester Digital 4 kb sector hd needs a special formating? 

I wouldn't think so, but you may have come across a compatibility issue that is more to do with FAT32 than the drive itself.  In any case, if the drives only get used on a Linux machine then you should consider using ext4 as the format.  You can also get ext4 support under windows by installing and ext4 driver from Sourceforge.


> 6) Why don't I see "SMART Status: Disk is healthy" in Samsung 1.5 TB?

Some drives don't support SMART, and some drives won't do it over USB.  You would need to do disk checks at least monthly on this drive as you won't get any warning about the drive failing until you actually start losing data.

Chris

---

### Post by paker on 2011-06-11
Thank you for kindly checking my setup. I really didn't know what I was selecting when I was installing the hard drives. I vaguely remember I had to run a 512 byte sector program first. Was it not necessary? Actually, potentially problematic?

Is this concern (512 vs 4k) limited to NTFS format? Is it a non-issue if I switch over to ext4?

Thanks.

---

### Post by VOT Productions on 2011-06-11
Use 512 byte. Don't worry about 4k.

---

### Post by paker on 2011-06-11
> **VOT Productions said:**
> Use 512 byte. Don't worry about 4k.

In other words, when I get a new WD20EARS (i am buying another), treat is just like any other hard drive and format it to NTFS (for my Windows laptop)?

OR DON'T BUY IT?

---

### Post by VOT Productions on 2011-06-11
Yes, format it normally.

---

### Post by paker on 2011-06-12
Thanks.

Now I remember what I did with the first WD20EARS. I used WD alignment software. Nothing to do with formating. And I used the software because the HD would be connected to my Windows XP laptop. 
Thanks.

---

