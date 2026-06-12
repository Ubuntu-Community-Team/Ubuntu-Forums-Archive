---
title: "Adding a second SATA hard disk"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by MaxVK on 2011-07-06
Hi. I'm using Lucid (10.04).
I have /home on a separate partition but only a single hard disk and I would like to add another hard disk to the machine. Currently the System Monitor shows /dev/sda1 as root and /dev/sda2 as /home.

**1) Ideally**
Id like to add the second hard disk and move my /home folder onto it completely, removing the old /home partition. This would then leave me with two disks, one for root (and swap) and one for /home.

**2) Otherwise...**
If moving /home is going to be a pain (By being a pain I mean taking too long - I work some odd hours and time to work on the system is tight) I don't mind just getting the other hard disk into the machine to use as storage for media etc, which would free up space in my /home folder.

Could anyone please explain the best (easiest/quickest) way to get things done properly. I'm not an Ubuntu novice and I'm happy editing files and using the console, but I'm more of a user than a guru.

Any help would be much appreciated.

regards

Max

---

### Post by coffeecat on 2011-07-06
If you don't want to move /home to your second hard drive, but use this for storing media files, then the simplest thing to do is:

1 - Physically install the drive.

2 - Use Gparted to create one partition on it, formatted ext4. Give it a suitable partition label as well.

3 - Edit /etc/fstab so that the new partition is mounted on bootup.

4 - Start using the partition for your media files. For convenience you could set up symlinks from the new partition to your home folder, if you wish.

One issue will be permissions in the new ext4 partition. By default, this will be owned by root and you will encounter permission denied errors when you first try to copy files to it, unless you do one of two things. The first is to use mount options in the fstab line to give you access as an ordinary user. The other, which is my preferred choice, is to chown the root of the filesystem of the new ext4 partition to your ownership. Then, a simple "defaults" in the fstab line suffices. 

Post back if you need help with any of this. If you do, post the output of these two commands:

```
sudo fdisk -lu
cat /etc/fstab
```

It won't tell us about your new drive but it will provide useful information about your system.

---

### Post by MaxVK on 2011-07-06
Thanks coffeecat, the info you asked for (New drive is NOT physically installed yet):

**sudo fdisk -lu:**
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046cf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58673151    29335552   83  Linux
/dev/sda2        58673152   293048319   117187584   83  Linux
/dev/sda3       293048320   312580095     9765888   82  Linux swap / Solaris
```

**cat /etc/fstab:**
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a2852ca4-33c8-40a6-b228-c99dfaa72b25 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=60ae0006-3bfd-4d0e-9938-0437039856a1 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=2dbe9e72-6ed8-4f07-b615-1f2421489859 none            swap    sw              0       0
```

Further information would certainly be helpful, thanks. If /home is not being moved it would be helpful if the new drive could be partitioned into two drives.

Thanks for your help

regards

Max

---

### Post by oldfred on 2011-07-06
I do not prefer the move /home to a new drive, and you should at least follow coffeecats suggestions. I use /mnt/data and links for all my data partitions/folders.

I suggest that each drive should have a fully configured operating system on that drive including booting from the MBR of that drive. Drives do fail and if part of the system is on two drives then one failure prevents you from booting either drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by coffeecat on 2011-07-06
@MaxVK, this is what I would suggest.

Install your drive into the machine and install Gparted to your Ubuntu system if not already done so. Open Gparted, and choose the new drive from the drop-down top-right. It will probably be /dev/sdb. It will probably show as all unallocated. Triple-check you have the correct drive showing because you are now going to make a partition table, which will effectively wipe it. Which you won't want if you have the wrong drive selected. Now Device (menu) -> Create Partition table. It will default to the mbr partition table which will be fine. Now create your two partitions, whatever sizes you want, formatted ext4 - Partition menu -> New. Since you want only 2 partitions, primary partitions will be fine. Choose a label for each partition as you create it. I will assume you will have "Part1" and "Part2" for illustration, but change these to what you want.

Remember that you need to click on Apply in Gparted before the partition changes are committed. Once you have created the partitions, close Gparted and open a terminal, and:

```
sudo mkdir /media/Part1
sudo mkdir /media/Part2
sudo blkid
```

Substitute your chosen partition labels for "Part1" and "Part2". I've suggested you make the mountpoint names the same as the partition labels because this keeps everything simple and tidy. You need to run the last command to get the UUIDs of the two new partitions. These are the long strings that you can see in fstab, for example:

```
UUID=60ae0006-3bfd-4d0e-9938-0437039856a1 /home           ext4    defaults        0       2
```

Now you need to edit /etc/fstab with:

```
gksudo gedit /etc/fstab
```

Add these two lines:

```
UUID=xxxxx-xxxx-xxxx-xxxx-xxxxx     /media/Part1     ext4     defaults     0 2
UUID=yyyyy-yyyy-yyyy-yyyy-yyyyy     /media/Part2     ext4     defaults     0 2
```

Substitute the actual UUIDs you derived from 'sudo blkid' for "xxxx..." and "yyyy....". Also substitute your partition labels for Part1 and Part2 in those two lines.

Save the edited /etc/fstab, and now:

```
sudo mount -a
```

Two icons will appear on the desktop labelled "Part1" and "Part2" (or whatever you have called them). One last thing to do. If you open those partitions now and try to copy files or create folders you will get a permission denied. So...

```
sudo chown yourusername: /media/Part1
sudo chown yourusername: /media/Part2
sudo chmod 777 /media/Part1
sudo chmod 777 /media/Part2
```

Again, substitute whatever labels you have chosen for Part1 and Part2, and your login name for "yourusername". Don't forget that trailing colon in the first two of those commands - it sets the default group.

Those commands change the ownership and permissions of the roots of the filesystems of the two partitions, not the mountpoints. You will now be able to copy files as wou wish.

I haven't covered symlinks, nor how to remove the desktop icons if you don't want them. Post back if you need any more.

Good luck!

---

### Post by oldfred on 2011-07-06
@coffeecat & OP

I also have many times suggested using 777 for total permissions. I was politely admonished by morbius1 with a better way. morbius1 is one who I have always relied on for mounting information.

I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable. May be partially as I include recursion so all files in the data partition inherit the permissions.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

sudo chmod -R a+rwX /data

---

### Post by MaxVK on 2011-07-06
Thanks very much coffeecat, you instructions have worked exactly as you suggested. Excellent.

oldfred: Point taken about moving /home - Ill remember that thanks, and now I'm wondering if the instruction you suggested would be the best way to handle the permissions.

I did read through the suggested post but I'm not sure that I understand fully what was being said! Does the (apparently) standard "sudo chmod 777 /media/Part1" make everything on the partition executable? Ill be storing media such as music and video on one partition and probably a whole host of stuff on the other.

In this situation (or any other specific situations) would the alternative command suggested (sudo chmod -R a+rwX /data) be a safer thing to do?

Many thanks for all input, it is much appreciated.

regards

Max

---

### Post by oldfred on 2011-07-06
I went back to see what I did myself and even though I have recommended 777, I used 776. But then I have manually changed a few scripts I have in some of my data to be executable.

Most of /home's default settings are 644, so you can use anything you want, just be aware of the risks to having too permissive of a setting.

---

### Post by coffeecat on 2011-07-06
> **oldfred said:**
> I also have many times suggested using 777 for total permissions. I was politely admonished by morbius1 with a better way. morbius1 is one who I have always relied on for mounting information.

I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable. May be partially as I include recursion so all files in the data partition inherit the permissions.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)


I absolutely agree that...

```
sudo chmod -R 777 /path/to/whatever
```

... is not a good idea, because it gives 777 permissions to every file and folder in the filesystem. However, I was advising MaxVK to do...

```
sudo chmod 777 /blah/blah
```

.... on an empty filesystem without recursion. There's an important difference. If you chmod or chown a mounted filesystem, you chown and chmod the root of the filesystem. I like to imagine the root of the filesystem as the grandaddy parent directory of everything. This enables you to create folders to your heart's content without needing root powers, and then fine-tune the permissions on the subordinate directories as one needs.

This business of chowning and chmodding the root of a filesystem seems to be little understood or known about. In my earlier post I suggested...


```
sudo chown username: /media/Part1
sudo chmod 777 /media/Part1
```

No recursion. If you then do...

```
ls -l /media
```

... you see that /media/Part1 appears to be owned by "username" and has permissions of rwxrwxrwx. But its not the /media/Part1 folder that has this ownership/permissions, it's the filesystem that's been mounted there. Unmount the partition and repeat 'ls -l /media' and you'll see that the /media/Part1 folder is still owned by root with the default permissions.

Interesting - and useful.

> **MaxVK said:**
> I did read through the suggested post but I'm not sure that I understand fully what was being said! Does the (apparently) standard "sudo chmod 777 /media/Part1" make everything on the partition executable? Ill be storing media such as music and video on one partition and probably a whole host of stuff on the other.

In this situation (or any other specific situations) would the alternative command suggested (sudo chmod -R a+rwX /data) be a safer thing to do?

No, "sudo chmod 777 /media/Part1" does not make everything on the partition executable because it's not a recursive command. It acts only on the root of the filesystem for the reasons I explain above. You have to use 777 rather than 666 because a directory (which is basically what the root of the filesystem is) needs to be executable in order to be [s]writeable[/s] **EDIT** - no, not writeable. I think they need the executable bit to be accessible. **End-EDIT** Look at the folders in your home folder. They're all "executable". You could use 770 or 755 or some other combination if you need to control group and other access, but 777 gives you open access to create the folders you need and then adjust their permissions to suit your needs.

I don't think a recursive chown is a good idea unless you already have some files and folders stored on the partition, when it may become necessary. My instructions were for chmodding and chowning a freshly formatted and empty partition. If you already have data on a partition, you need to be more nuanced with your chmodding and chowning - perhaps doing recursive operations on selected sub-folders.

---

### Post by MaxVK on 2011-07-06
> My instructions were for chmodding and chowning a freshly formatted and empty partition
Which is exactly what I have done, so thank you, things appear to be working exactly as I expected them to.

I wont pretend to fully understand the arguments back and forth about the best way to set permissions, so until I get a clearer understanding Ill leave things exactly as they are.

Many thanks for all your help.

regards

Max

---

