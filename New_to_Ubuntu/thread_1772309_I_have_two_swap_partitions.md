---
title: "I have two swap partitions?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by TerribleLIar on 2011-05-31
I'm just curious if I have an extra swap parition that isn't being used and probably shouldn't be there. Under blkid, I have two partitions listed with the TYPE="swap". Their locations are /dev/sda5 and /dev/sda7. Under /etc/fstab, the only swap partition listed is the /dev/sda7 one. What is the /dev/sda5 swap partition doing there? Would there be anything else that would use it? Each swap partition is 1.1GB large, I have 1 GB RAM, and I only have Ubuntu 11.04 and Win7 on my computer.

If it is found to be useless, is it easy to allocate that space to the main Ubuntu partition without any issues?

---

### Post by ratcheer on 2011-05-31
Yes, it is no problem at all for your system to use multiple swap partitions. I used two for a long time, thinking that each Linux on my system needed its own swap space. When I noticed that both instances were using both swap spaces, I removed one of them with no issues.

Tim

---

### Post by oldfred on 2011-05-31
Did you do two auto installs and each created a swap? Yes you can delete one or the other, but have to have the correct UUID in fstab for the one you keep. But where on the drive is your Ubuntu install. I generally do not like moving partitions left to expand as it moves all data. Moving right side to expand is much easier. So which swap is adjacent to main install and which side of main install is it on?

Post your sudo blkid or sudo fdisk -lu and fstab. And which partition is your Ubuntu installed in.

---

### Post by TerribleLIar on 2011-05-31
I did reinstall Ubuntu at one point because I thought I messed it up, and I didn't have anything on it so a fresh install was easier. Maybe sda4 and 5 were the older installation and it didn't delete the swap partition for whatever reason. I'm guessing by moving left or right you mean the information from fdisk? Like moving a partition that starts in a higher sector to a lower sector would be moving left?

```
sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="DCAA0584AA055D00" TYPE="ntfs" 
/dev/sda2: UUID="A4DE0A3DDE0A07EE" TYPE="ntfs" 
/dev/sda5: UUID="fc7d7534-ce5c-4598-8b91-3186243a8aad" TYPE="swap" 
/dev/sda6: UUID="5fe24306-c4a5-4199-bc18-62be5e730ff5" TYPE="ext4" 
/dev/sda7: UUID="e83ac6f3-50c2-4864-87a1-427e3c16d5e9" TYPE="swap" 

```

```
sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   293367895   146580524    7  HPFS/NTFS
/dev/sda3       293369854   390721535    48675841    5  Extended
/dev/sda5       388644864   390721535     1038336   82  Linux swap / Solaris
/dev/sda6       293369856   386566143    46598144   83  Linux
/dev/sda7       386568192   388644863     1038336   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e83ac6f3-50c2-4864-87a1-427e3c16d5e9 none            swap    sw              0       0
# automatically mount my Win7 partition
UUID=A4DE0A3DDE0A07E    /media/A4DE0A3DDE0A07E    ntfs    defaults    0    0
```

---

### Post by oldfred on 2011-05-31
It looks like sda5 is after sda7. So if you want to merge the space with your Ubuntu install then you will want to delete sda7. But sda7 is the one you mount in fstab, so you will have to update fstab with the UUID of sda5.

Then you can just expand your sda6 partition right into the free space created by the deletion of sda7. 

I would first change UUID in fstab and make sure that works with sda5. then from liveCD delete sda7 and expand sda6. You have to use liveCD and will have to swapoff on swap partition(s) to allow editing of any logical partition in the extended partition.

# modify fstab to mount directory
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a

Be sure to run the mount -a command. If no errors it just remount everything. If errors in editing fstab it will tell you and you have to fix before rebooting or you may not be able to reboot.

---

### Post by TerribleLIar on 2011-05-31
Thanks! Works great. Well, I didn't do the LiveCD part yet, but it looks simple enough. It's already using the other swap space, so it shouldn't have any issues.

---

