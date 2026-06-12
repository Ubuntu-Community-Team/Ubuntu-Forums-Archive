---
title: "Moving Ubuntu to a Second HDD"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Zintha on 2010-04-23
I am currently running Lucid Lynx on a computer which also has Windows XP setup as a duel boot on a single HDD.
(partitioned) 
50gb to Ubuntu
100gb to XP.

I started running out of space pretty quickly to be honest so I dug through my box of computer parts and found another 160gb HDD to use, in full working order.

So, how do I take my Ubuntu from the 1st drive onto the 2nd so in the end i've got:

XP on 1st drive
Ubuntu on 2nd drive.

In advance, thank you for your help.

edit: Just thought of it but I do not have access, nor the will if avoidable, to reinstall XP onto the new drive. I'd rather not touch that and just move Ubuntu to be honest.

---

### Post by undecim on 2010-04-23
easiest thing to do would probably be to do this:
[LIST=1]
[*]install the second drive.
[*]make a swap and ext4 partition on it using GParted from a live CD
[*]Move your home directory to the new ext4 partition
[*]clone each data partition on your current drive to a file on your new drive, just in case the next step goes awry. (using dd and gzip. If you want exact instructions, post the output of "sudo fdisk -l") 
[*]With GParted again, remove the swap partition on your current drive and shrink your Ubuntu partition to ~10GB
[*]Add an entry in /etc/fstab for your new drive as /home/ and change the swap entry (I need your current /etc/fstab and the output of "sudo blkid" to give you exact instructions)
[/LIST]

The end result will be 10GB for Ubuntu on your first drive, with the rest of that drive given to XP, and the other drive will store your home directory and swap.

This way, you don't have to reconfigure grub, and you get a minor performance boost from having / and swap on different drives and /tmp and /home/ on different drives, as well as the freedom that a separate home partition gives you.

---

### Post by Zintha on 2010-04-23
How big do the swap and ext4 partitions have to be and what are they exactly?

First thing you wanted:
> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13033   104687541    7  HPFS/NTFS
/dev/sda2           13034       19452    51560617+   5  Extended
/dev/sda5           13034       19184    49407876   83  Linux
/dev/sda6           19185       19452     2152678+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4bbeb05a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32


Second thing you wanted:
> /dev/sda1: UUID="CEE069D2E069C0F7" TYPE="ntfs" 
/dev/sda5: UUID="15a37ae3-976b-4331-8125-b57b0c2b2f47" TYPE="ext4" 
/dev/sda6: UUID="327f8da9-2953-41f8-94c7-e4f08709192c" TYPE="swap" 
/dev/sdb1: UUID="199E-9ACF" TYPE="vfat" 


Let me know if you need more info, sorry for asking for a walk through of the entire process but i'm still new to this and don't want to mess it up!

---

### Post by undecim on 2010-04-23
alright then.

1: once you have the second drive in the computer, boot a live CD and use GParted to create a swap partition and an ext4 partition. The swap partition should be the same size as your current swap partition, (or depending on how much ram you have and whether or not you use hibernation, you may not even need one). The ext4 partition should fill up the rest of the drive.

2: Next, move your home directory to that drive: Open both your Ubuntu and your new partitions in a file manager to mount them, then open a terminal and run
```
sudo cp -ar /media/ubuntu/home/* /media/new/"
```
where /media/ubuntu and /media/new are the paths to your Ubuntu and new partitions respectively. 

3: Next, we clone your data partitions. This will take a while. If you already have a backup of each of your partitions, you can skip this step. Start by ejecting every drive except your new ext4 partition. Then run these commands in a terminal
```
sudo dd if=/dev/sda1 | gzip -c > /media/new/sda1.gz
sudo dd if=/dev/sda5 | gzip -c > /media/new/sda5.gz
```
again, where /media/new/ is the path to your new partition.

4: With GParted, remove the swap partition (sda6) on your current drive and shrink your Ubuntu partition to ~10GB. Shrinking your Ubuntu partition will involve resizing sda2, and then sda5, since sda5 is a logical partition inside of sda2

5:And finally, we fix fstab. You need to add this line to /etc/fstab:
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /home/ ext4 defaults 0 2
``` where xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is the UUID you see for the ext4 partition on sdb when you run "sudo blkid"

To fix the swap partition, find the line that includes the word "swap" and replace the UUID with the one you see for the swap partition on sdb when you run "sudo blkid"

Then, you can reboot, and if everything goes well, you should have more space in your home directory and in XP. Once you have verified that everything works, you can delete the "sda1.gz" and "sda5.gz" files from /home/

---

### Post by oldfred on 2010-04-24
undecim has given you a lot of good advice on moving. 

But I just installed the RC to a partition I already had set up and it took 9 minutes for the full install. I did not link it to my current /home as I am not yet converting, just testing. I think a clean install avoids all sorts of issues. You would still have to move /home, but that is relatively easy.

I always think it is better to keep a small root partition and have /home or even better a /data partition that has all your data. I now have three root partitions (9.04,9.10 & RC) and my current Karmic only uses 5-6GB without /home nor data. But /home became only 1GB when I moved all the data to a /data partition.

---

### Post by jaycee23 on 2010-04-24
> **oldfred said:**
> undecim has given you a lot of good advice on moving. 

But I just installed the RC to a partition I already had set up and it took 9 minutes for the full install. I did not link it to my current /home as I am not yet converting, just testing. I think a clean install avoids all sorts of issues. You would still have to move /home, but that is relatively easy.

I always think it is better to keep a small root partition and have /home or even better a /data partition that has all your data. I now have three root partitions (9.04,9.10 & RC) and my current Karmic only uses 5-6GB without /home nor data. But /home became only 1GB when I moved all the data to a /data partition.

Oldfred - this sounds very interesting to me as I'm about to do a fresh install of 10.04. I have 9.10 working well as a Win7 dual boot with Ubuntu split into root , home and swap partitions.
Are there any simple instructions so I can try to set things up like you've discussed?

---

### Post by Zintha on 2010-04-24
I haven't yet tried this but will do sometime today! Hopefully no glitches, just wanted to post so you don't think i've got the solution then ran away without a thanks.

---

### Post by oldfred on 2010-04-24
for jaycee23 but it may apply to Zintha so it is not a total hijack.

If you just want to create another root with 10-20 GB then you use manual install and use your existing (do NOT format) /home and swap. I have multiple drives so I have different boots set in each MBR but each install finds all the others so you can boot any system.

For a bigger change to convert to a shared data partition:
How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by Zintha on 2010-04-24
> **undecim said:**
> alright then.

1: once you have the second drive in the computer, boot a live CD and use GParted to create a swap partition and an ext4 partition. The swap partition should be the same size as your current swap partition, (or depending on how much ram you have and whether or not you use hibernation, you may not even need one). The ext4 partition should fill up the rest of the drive.

2: Next, move your home directory to that drive: Open both your Ubuntu and your new partitions in a file manager to mount them, then open a terminal and run
```
sudo cp -ar /media/ubuntu/home/* /media/new/"
```where /media/ubuntu and /media/new are the paths to your Ubuntu and new partitions respectively. 

3: Next, we clone your data partitions. This will take a while. If you already have a backup of each of your partitions, you can skip this step. Start by ejecting every drive except your new ext4 partition. Then run these commands in a terminal
```
sudo dd if=/dev/sda1 | gzip -c > /media/new/sda1.gz
sudo dd if=/dev/sda5 | gzip -c > /media/new/sda5.gz
```again, where /media/new/ is the path to your new partition.

4: With GParted, remove the swap partition (sda6) on your current drive and shrink your Ubuntu partition to ~10GB. Shrinking your Ubuntu partition will involve resizing sda2, and then sda5, since sda5 is a logical partition inside of sda2

5:And finally, we fix fstab. You need to add this line to /etc/fstab:
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /home/ ext4 defaults 0 2
``` where xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx is the UUID you see for the ext4 partition on sdb when you run "sudo blkid"

To fix the swap partition, find the line that includes the word "swap" and replace the UUID with the one you see for the swap partition on sdb when you run "sudo blkid"

Then, you can reboot, and if everything goes well, you should have more space in your home directory and in XP. Once you have verified that everything works, you can delete the "sda1.gz" and "sda5.gz" files from /home/
Did all the partitions, however step 2 I typed in:
sudo cp -ar /media/ubuntu/home* /media/new"
and it doesn't seem to do anything, unless i'm misunderstanding?

---

### Post by Zintha on 2010-04-24
Sorry for needing extra help upon extra help, I don't mean to ask you to do everything for me. 

I'm guessing /media/ isn't supposed to be /media/ and is supposed to be the sbd1 or sba2 or the drive names? If so, I don't understand the best way to find out which is which?
(edit: On that note, I know what Sudo is, btu what is CP (copy?) and -ar (which I have no idea) and how does the * and the " at the end effect things?
On the plus side, learning Gparted pretty well!

---

### Post by oldfred on 2010-04-24
You can always get answers to what command are by typing - man command
```
man cp
```

cp is copy and various options exist r is recursive meaning copy subdirectories. -a is the same as -dpR, so you should not need the r with the -a. p perserves attributes which is critical for permissions and ownership. -d will copy files not symbolic links.

The /media/ may depend on how you mounted it. /media is usually the default. * is the same as in windows meaning everything or all files.

---

### Post by undecim on 2010-04-24
> **Zintha said:**
> Sorry for needing extra help upon extra help, I don't mean to ask you to do everything for me. 

I'm guessing /media/ isn't supposed to be /media/ and is supposed to be the sbd1 or sba2 or the drive names? If so, I don't understand the best way to find out which is which?
(edit: On that note, I know what Sudo is, btu what is CP (copy?) and -ar (which I have no idea) and how does the * and the " at the end effect things?
On the plus side, learning Gparted pretty well!

cp = copy

-ar = "archive" and "recursive" options. It preserves permissions and extra data and does all the files in all the folders that you copy.

you need to replace /media/ubuntu and /media/new with the mount points of the partitions. You can run "mount" to see what the mount points are. replace /media/ubuntu with the mountpoint for /dev/sda5 and /media/new with the mount point for /dev/sdb1 (or sdb2, if you have the ext4 partition after the swap)

---

