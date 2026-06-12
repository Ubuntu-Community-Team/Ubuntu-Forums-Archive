---
title: "two linux swap partitions"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by mr.xulu on 2011-06-10
Hi! I'm using a neo laptop on dual boot with ubuntu and windows xp. until two days ago, i had lucid which i decided to replace with natty. At one point during installation I was given several options. I chose option number 1 which was, "erase ubuntu 10.04.2 and reinstall".

Now when I type "sudo fdisk -l" on terminal to list my partitions i get this:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85218521

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9730    37192908    f  W95 Ext'd (LBA)
/dev/sda5            5100        8054    23728701+   7  HPFS/NTFS
/dev/sda6            9653        9730      613376   82  Linux swap / Solaris
/dev/sda7            8054        9327    10231808   83  Linux
/dev/sda8            9328        9653     2610176   82  Linux swap / Solaris

It seems I have two linux swap partitions now.

Are two needed? If I only need one, is there a way to delete one swap partition and join it with my main natty partition?

Thanks a lot :)

---

### Post by TerribleLIar on 2011-06-10
I had the exact same problem. Topic is here.  [http://ubuntuforums.org/showthread.php?t=1772309&highlight=i+have+two+swap+partitions%3F](http://ubuntuforums.org/showthread.php?t=1772309&highlight=i+have+two+swap+partitions%3F)

Make sure you're only using one swap partition. Check /etc/fstab (enter sudo gedit /etc/fstab in the terminal) to make  sure only one swap is mounted. It's likely the /dev/sda8 one. The  easiest way to merge the extra swap with the Linux partition is to start  using the /dev/sda6 swap partition. Do "sudo blkid" and put the UUID in  place of the /dev/sda8 one (unless the sda6 partition is the only  already being used). Then merge it with the Linux partition through  LiveCD. That's just a quick and dirty summary of what oldfred said to do. Read his posts in my topic for a more precise explanation.

---

### Post by Paqman on 2011-06-10
> **TerribleLIar said:**
> 
Make sure you're only using one swap partition.

There's no reason you couldn't use two or more swap partitions, the system will use as many as you give it. It's just a bit of a waste of space.

But yes, edit /etc/fstab to ensure it shows only the one you want to keep, and use the Disk Utility or Gparted to delete the other one and expand the adjacent partition into the freed space.

---

### Post by mr.xulu on 2011-06-10
Thanks TerribleLIar and Paqman!

"edit /etc/fstab to ensure it shows only the one you want to keep, and use the Disk Utility or Gparted to delete the other one and expand the adjacent partition into the freed space."

TerribleLIar and Paqman,

Can i ask for specific instructions (exact commands for terminal?) how to "edit /etc/fstab" and how to use disk utility?

Thanks again! :)

---

### Post by nitstorm on 2011-06-10
> **mr.xulu said:**
> 

Can i ask for specific instructions how to "edit /etc/fstab" and how to use disk utility?


What you need to do is look at [this link]("https://help.ubuntu.com/community/Fstab") at the default config - (from the link mentioned) your */etc/fstab *will have something similar to this for the swap area:```
# /dev/sda6 UUID=cee15eca-5b2e-48ad-9735-eae5ac14bc90  none  swap  sw  0  0
```Make sure you know what partition is getting used in fstab for the swap. Then click on the top left button that launches the unity panel and type in "Disk Utility" and make a new partition of the unused swap partition or extend it to another partition. I am not sure if "Disk Utility" supports extension of an existing but I am sure gparted does. you can install gparted by```
sudo apt-get install gparted
``` and launch it the same way as you launch "Disk Utility" with the Unity Panel

---

### Post by mr.xulu on 2011-06-10
Thanks nitstorm! I'll try it :)

---

### Post by mr.xulu on 2011-06-10
Hi nitstorm!

I typed "sudo blkid" on terminal and I got this:

/dev/sda1: UUID="40E812B5E812A964" TYPE="ntfs" 
/dev/sda5: UUID="6E9057189056E5DD" TYPE="ntfs" 
/dev/sda6: UUID="713f3da6-9fd9-4aa6-bb7a-0b7e04ffe4d5" TYPE="swap" 
/dev/sda7: UUID="20a6316d-3548-4b62-8b74-bfc8add62b10" TYPE="ext4" 
/dev/sda8: UUID="2231a596-9727-4875-8acc-e3cde2122c56" TYPE="swap" 

I typed "gedit /etc/fstab" and I got this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=2231a596-9727-4875-8acc-e3cde2122c56 none            swap    sw              0       0

From the last command it seems natty is using /dev/sda8/ for the /etc/fstab and /dev/sda6 is the unused one. while /dev/sda7 is the main natty partition. Did I get it right?

I've installed gparted. How do I use it to "make a new partition of the unused swap partition or extend it to another partition"?

I'd like to merge the unused swap to become part of my main natty partition.

Thanks again :)

---

### Post by oldfred on 2011-06-11
You will not be able to use gparted from your working Ubuntu as you cannot change mounted partitions. Any partition inside the extended partition in effect mounts the entire extended.

You need to use the gparted on a liveCD and even then you have to click on the swap partition(s) and right click swap off to unmount them. LiveCDs often mount the swap if found to speed things up.

Change this before using liveCD to delete partition.
gksudo gedit /etc/fstab

Change the UUID of the swap to sda6. If you keep the sda8 swap and delete sda6 then you have to move partition left. Very slow as all data has to be copied and a bit more risk. But if you change fstab and then delete sda8, it becomes very easy to expand sda7 right into that free space.

Edit:
Anytime you manually edit fstab, you want to be sure it will be ok when you reboot.

sudo mount -a

It will just remount with the changes now mounted to mtab. If it returns any errors you need to fix before rebooting or you may not be able to reboot.

---

### Post by mr.xulu on 2011-06-11
Thanks oldfred! I'm trying out your suggestion. I typed "gksudo gedit /etc/fstab" and got the code below:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/[COLOR="Red"]sda8[/COLOR] during installation
UUID=2231a596-9727-4875-8acc-e3cde2122c56 none            swap    sw              0       0

I just wanna clarify how to edit the above code. Do i just go the line where it says "sda8" (in red fonts) and type "sda6" over it to be able reassign sda6 as the /etc/fstab?

Thanks again :)

---

### Post by Paqman on 2011-06-11
> **mr.xulu said:**
> 
I just wanna clarify how to edit the above code. Do i just go the line where it says "sda8" (in red fonts) and type "sda6" over it to be able reassign sda6 as the /etc/fstab?


No, that line is just a comment (you can tell from the # at the start). You want the line below it that starts UUID=. Replace UUID=2231a596-9727-4875-8acc-e3cde2122c56 with /dev/sda6 (or the correct UUID for sda6) and save the file.

---

### Post by mr.xulu on 2011-06-11
Thanks everybody! I've edited the /etc/fstab. Please see last line of code:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=713f3da6-9fd9-4aa6-bb7a-0b7e04ffe4d5 none swap sw 0 0


I got this with "sudo fdisk -l":

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85218521

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9730    37192908    f  W95 Ext'd (LBA)
/dev/sda5            5100        8054    23728701+   7  HPFS/NTFS
/dev/sda6            9653        9730      613376   82  Linux swap / Solaris
/dev/sda7            8054        9653    12849152   83  Linux


I hope I did it right.

I was able to delete /dev/sda8 thru liveusb and merge it with the main natty partition.

In case I made an error editing /etc/fstab, is there a way to find out if the new swap was not assigned properly?

Thanks for everything! :)

---

### Post by oldfred on 2011-06-11
I left off one command that anytime you manually edit fstab you should run to make sure you can boot. Obviously if you rebooted you edited it correctly but this checks to make sure it is ok. I will edit above post just in case  someone else sees this.

sudo mount -a

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
To see swap in use:
```

free
```If you have 2GB of RAM or more swap may not show any use. I have 4GB and right now am just running Firefox, gedit & terminal:

f```
red@fred-MavericDT:~$ free
             total       used       free     shared    buffers     cached
Mem:       4056196    3987280      68916          0    1828612    1315764
-/+ buffers/cache:     842904    3213292
Swap:      6144820          0    6144820

```

---

### Post by mr.xulu on 2011-06-11
Thanks a lot oldfred! :)

---

