---
title: "HELP....I am screwed...changing form 8.10 to 9.04"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-05
I decided to update my wife's PC to 9.04. She was dual booting with XP. Easy I thought...just press the upgrade button and away we go....HAH!

The screen saver kicked in the middle of the upgrade and locked everything up....I had to restart...and of course the upgrade had only been part way through....

So now I am uploading from the CD....I want to keep the dual boot...and when I clicked to install alongside XP, it was unable to save whatever it had written and has dumped me into the advanced prepare partitions.

I now have 4 possible partitions showing.

sda, sda1 (ntfs), sdb and sdb1 (Fat 32)...only sda1 and sdb1 have format boxes....It needs me to choose a place to boot from..what do I do now?

She is goon kill me when she gets back in a couple of hours!

---

### Post by apostate on 2009-05-05
> **dunbrokin said:**
> I decided to update my wife's PC to 9.04. She was dual booting with XP. Easy I thought...just press the upgrade button and away we go....HAH!

The screen saver kicked in the middle of the upgrade and locked everything up....I had to restart...and of course the upgrade had only been part way through....

So now I am uploading from the CD....I want to keep the dual boot...and when I clicked to install alongside XP, it was unable to save whatever it had written and has dumped me into the advanced prepare partitions.

I now have 4 possible partitions showing.

sda, sda1 (ntfs), sdb and sdb1 (Fat 32)...only sda1 and sdb1 have format boxes....It needs me to choose a place to boot from..what do I do now?


She is goon kill me when she gets back in a couple of hours!

Ok partner, first off, do NOT format the ntfs partition. That is Windows!
Next, If sdb is only divided into 1 partition, sdb1 (fat 32) it would seem your Ubuntu was on a second drive, formatted as fat32? Is this right? I am surprised there are no ext3 partitions. Please confirm.

---

### Post by ptn107 on 2009-05-05
I believe sda1 is your XP partition and sdb1 is for Ubuntu, why it's formatted fat32 I have no idea.

---

### Post by dunbrokin on 2009-05-05
Yes, my guess is that the fat32 is where the old Ubuntu (which I would like to keep....coz then I will only be half dead...when she finds out)...there is nothing of the Type ext ...only ntfs and fat32.


I am happy to keep the fat 32 for the short term...until I can convince her to dump Windows...

---

### Post by apostate on 2009-05-05
> **dunbrokin said:**
> Yes, my guess is that the fat32 is where the old Ubuntu (which I would like to keep....coz then I will only be half dead...when she finds out)...there is nothing of the Type ext ...only ntfs and fat32.

Alrighty. Lets click on that first partition, and get the little dialog box. The drop down might say "Do Not Use this Partition". Change that to type "ntfs", and mountpoint to /windows. DO NOT FORMAT!

Next, let's click on that sdb1, and delete it. The create a new partition there of type "swap". Make it about as many MB as the machine has RAM. So if it has 512, make the swap space 512. We'll then click on sdb and create a new partition, taking up the whole rest of the drive. Format this one as ext3, not fat32. Make the mountpoint /

Now you should be able to let her rip.

sda1 /windows ntfs  format NO
sdb1 swap     swap
sdb2 /        ext3  format YES

Make sense?

---

### Post by ktrnka on 2009-05-05
[From a live cd]
Please paste the results of this: In a terminal. Applications>Acc>Terminal

```
sudo fdisk -l
```

Ok once we have figured out which partition is your ubuntu partition, you will probably want to run: (assuming it's sdb1)

```
sudo fsck /dev/sdb1
```

If there is a problem with fsck and your ubuntu partition's id tag has been changed, you will need to change it with fdisk.

Moving on,

You should be able to mount the ubuntu partition.

```
mkdir TEMP
```
```
sudo mount /dev/sdb1 TEMP
```

Then we need to run:

```
sudo mount --bind /proc TEMP/proc
```
```
sudo mount --bind /dev TEMP/dev
```
```
sudo mount --bind /tmp TEMP/tmp
```

Now you can chroot to the TEMP folder and continue the upgrade while still using the live cd.

```
sudo chroot TEMP
```

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

---

### Post by dunbrokin on 2009-05-05
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce10ce10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 4005 MB, 4005527552 bytes
32 heads, 63 sectors/track, 3880 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x2d0c13e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3880     3911008+   b  W95 FAT32

---

### Post by ktrnka on 2009-05-05
It appears as though your second drive is only 4GB? Is that the actual size?

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> It appears as though your second drive is only 4GB? Is that the actual size?


I guess that was the size when I originally set it up....I have been having out of memory issues with it when setting up Jaunty...so I guess I must have only set it at 4GB...not sure why really.

---

### Post by dunbrokin on 2009-05-05
ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

---

### Post by rzrgenesys187 on 2009-05-05
> **ktrnka said:**
> It appears as though your second drive is only 4GB? Is that the actual size?

It seems like that would be a flash drive or something

---

### Post by ktrnka on 2009-05-05
It needs to be a partition number:

```
sudo fsck /dev/sdb**1**
```

---

### Post by ktrnka on 2009-05-05
> **rzrgenesys187 said:**
> It seems like that would be a flash drive or something

Yea I was thinkin that or a CF card.

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> It needs to be a partition number:

```
sudo fsck /dev/sdb**1**
```

ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by dunbrokin on 2009-05-05
Ah...bugger...my Toshiba 4G USB drive is plugged in at the back....sorry :(

---

### Post by ktrnka on 2009-05-05
Oh so we are trying to find the missing ubuntu partition?

---

### Post by dunbrokin on 2009-05-05
Yes please!

---

### Post by ktrnka on 2009-05-05
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

Look @ the Lost Partition section

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

Look @ the Lost Partition section


I am hoping I have not written over it....how do I find out?

---

### Post by ktrnka on 2009-05-05
Those few utilities should be able to recover your lost partition. If none of them work, it was probably written over but you never know till u try.

---

### Post by dunbrokin on 2009-05-05
I would appreciate if somebody could walk me through this....it seems very complicated...

---

### Post by ktrnka on 2009-05-05
Ok open up a terminal:

```
sudo parted /dev/sda
```

Then post the results here

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> Ok open up a terminal:

```
sudo parted /dev/sda
```

Then post the results here

It just says welcome to Gnu Parted Type 'help' to view a list of commnds
(parted)

---

### Post by ktrnka on 2009-05-05
Ok now after running parted

```
rescue START END
```

If it prompts you to add a partition, say yes.

Once it is done, run this in a new terminal:

```
sudo fdisk -l
```

and paste the results here again.

---

### Post by dunbrokin on 2009-05-05
(parted) print list,all                                                   
Model: ATA FUJITSU MHV2080A (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  80.0GB  80.0GB  primary  ntfs         boot 


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> Ok now after running parted

```
rescue START END
```

.

Error:Invalid number

---

### Post by dunbrokin on 2009-05-05
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce10ce10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

---

### Post by ktrnka on 2009-05-05
```
rescue 0 80GB
```

I think that will work. Did u originally install Ubuntu with the WUBI installer or what?

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> [CODE]
. Did u originally install Ubuntu with the WUBI installer or what?


Yes I think so....

---

### Post by dunbrokin on 2009-05-05
> **ktrnka said:**
> ```
rescue 0 80GB
```

?

It did something....too quick to see...and then came back with 

(parted)

---

### Post by ktrnka on 2009-05-05
type ```
print
``` and/or do another ```
sudo fdisk -l
```

I hope this works as I have no experience with the WUBI installer. Sorry.

---

### Post by ktrnka on 2009-05-05
It appears as though the WUBI uses a virtual disk within the NTFS partition so.... you will have to repair windows. The last thing to try would be:

```
sudo ntfsfix /dev/sda1
```

Then try rebooting.

It should clear the NTFS journal. *Good Luck* I've gotta get some sleep.

If this does not fix it, you will need a windows cd to execute chkdsk /f on your C: drive (This is where Windows recovery comes into play)

Good Night!

---

### Post by DJonsson2008 on 2009-05-05
With being able to get good hard drives, sometimes for less than
40$, combined with Hard drive slide drawers, booting from USB 
external drives and other such options, I don't understand why
people wrestle with the nuances and foibles of dual booting on
the same hard drive. 

Yes its possible in theory and practice but it seems like it
opens of a realm of uncertainty and possible problems 
to those who don't have a 300% understanding of 
Gparted and other utils. 

If you manage to recover your data on this hard drive maybe
consider getting a separate drive for your Ubuntu usage, it 
makes life a lot simpler. And if you work with a 2 drive system
be sure to unplug the 2nd drive during initial Ubuntu formating.

---

### Post by DJonsson2008 on 2009-05-05
On second thought if you could get your hands on another
HD and install Ubuntu on it, then after reboot with the
old crashed OS install attached it could provide a pathway
to recovering the data on the problem drive.

---

### Post by matthewbpt on 2009-05-05
Am I right that this was a Wubi install? If so check the root drive of your windows install, C:\ubuntu\disks\, check that folder, what files are in that folder? If this was a wubi install then this should have some large files in it which are 'virtual disks,' this is where Ubuntu resides, and not in any of the physical paritions. Try runing a checkdisk on your C drive for errors the disks arent there. My girlfriend once had a problem where she couldn't boot into her Wubi install because the laptop shut down unsafely, so there was data corruption in her drive. Running the windows checkdisk fixed the curruption, but it moved the disk files in C:\ubuntu\disks\ to a hidden folder C:\found.000 which was protected and couldn't be accesesed by her user, I moved these back to the C:\ubuntu\disks\ folder using an ubuntu live cd, and voila Ubuntu would now boot.

If you manage to do this then you should be able to get to the grub menu, but you still won't be able to boot to Ubuntu because your update failed before it was finished, there is a way to fix this though, I know because I had a similar problem with one of my laptops crashing during an update. What you have to do is choose recovery mode in the grub menu, then after all the kernel messages a menu will pop up, and you select "fix broken packages,' then let it fix the packages, after this is done the menu will pop up again, select 'root shell with networking', then in the root menu run the command 'apt-get upgrade', then type 'reboot' when it finishes upgrading. This should fix the problem (worked for me at least).

Hope this helps!

---

### Post by dunbrokin on 2009-05-05
> **matthewbpt said:**
> Am I right that this was a Wubi install? If so check the root drive of your windows install, C:\ubuntu\disks\, check that folder, what files are in that folder? If this was a wubi install then this should have some large files in it which are 'virtual disks,' this is where Ubuntu resides, and not in any of the physical paritions. Try runing a checkdisk on your C drive for errors the disks arent there. My girlfriend once had a problem where she couldn't boot into her Wubi install because the laptop shut down unsafely, so there was data corruption in her drive. Running the windows checkdisk fixed the curruption, but it moved the disk files in C:\ubuntu\disks\ to a hidden folder C:\found.000 which was protected and couldn't be accesesed by her user, I moved these back to the C:\ubuntu\disks\ folder using an ubuntu live cd, and voila Ubuntu would now boot.

If you manage to do this then you should be able to get to the grub menu, but you still won't be able to boot to Ubuntu because your update failed before it was finished, there is a way to fix this though, I know because I had a similar problem with one of my laptops crashing during an update. What you have to do is choose recovery mode in the grub menu, then after all the kernel messages a menu will pop up, and you select "fix broken packages,' then let it fix the packages, after this is done the menu will pop up again, select 'root shell with networking', then in the root menu run the command 'apt-get upgrade', then type 'reboot' when it finishes upgrading. This should fix the problem (worked for me at least).

Hope this helps!

I wish I had known this earlier....I had to do a clean boot eradicating windows (much to my wife's dismay as there was one or two things she still used).....I think she is in the process of forgiving me....phew!

---

