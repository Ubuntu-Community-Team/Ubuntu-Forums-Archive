---
title: "fstab, 4 hard drives, confused"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Slownis on 2010-04-18
My computer has 4 hard drives.  Here is my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  defaults                          0  0  
# / was on /dev/sda1 during installation
UUID=e68dd4e4-549f-45ca-9194-90a298f44651  /               ext4  errors=remount-ro                 0  1  
# swap was on /dev/sda5 during installation
UUID=102bdc75-89fe-4681-9459-1ed5f396bb75  none            swap  sw                                0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8          0  0  
/dev/sdb2                                  /media/sdb2     ntfs  defaults                          0  0  
/dev/sda2                                  /media/sda2     ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sdc1                                  /media/sdc1     ext3  errors=remount-ro,users           0  0  

I have Palimpsest Disk Utility up and it shows my biggest drive mounted on sda1.  I can mount and unmount fine and it shows up in the UI.

But then I load up 'Storage Device Manager' and When I click on sda1, it gives me the info for sdb2 (an NTFS drive).  When I click on SDB2, it gives me the same info.  Why does 'Storage Device Manager' seem to be confused?

Also, I used to be able to look at SMART data in Palimpsest disk Utility, but now it always says 'SMART is not available' for all drives???

---

### Post by Slownis on 2010-04-18
In addition, when I click on 'Places' menu, it shows 'sda2', but there is nothing there, and it gives an error if I try to mount it.

Whenever I reboot, only the system drive and the SDB1 drive are automatically mounted.  I would like all 4 drives to automatically mount.

Edit:  Removing the line that starts /dev/sdb2  fixed the 'sda2' issue, but Storage Device Manager is confused about sda1, and I still cant look at the SMART data.

---

### Post by Penguin Guy on 2010-04-18
Could you [run]("http://www.psychocats.net/ubuntu/terminal") [FONT="Courier New"]sudo fdisk -l[/FONT] in the terminal (enter your password if prompted) and post the output back here please?

---

### Post by Slownis on 2010-04-18
> **Penguin Guy said:**
> Could you [run]("http://www.psychocats.net/ubuntu/terminal") [FONT=Courier New]sudo fdisk -l[/FONT] in the terminal (enter your password if prompted) and post the output back here please?

johnw@johnw-desktop:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045b39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       77825   625129281   83  Linux

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4414f4ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           3       12921    97667640    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7f7e7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4658    37415353+  83  Linux
/dev/sdc2            4659        4863     1646662+   5  Extended
/dev/sdc5            4659        4863     1646631   82  Linux swap / Solaris

Disk /dev/sdd: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e185a70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3736    30009388+  83  Linux
johnw@johnw-desktop:~$

---

### Post by Morbius1 on 2010-04-18
The only command that is going to display the uuid and /dev/sdxx for all your partitions is as follows:

**sudo blkid -c /dev/null**

And BTW, don't use any utility, regardless of who recommends it, that generates a line in fstab that looks like this:
>  /dev/sda2                                  /media/sda2     ntfs  nls=iso8859-1,[COLOR=Blue]ro[/COLOR],users,[COLOR=Blue]umask=000 [/COLOR] 0  0  

---

### Post by Drenriza on 2010-04-18
i dont get some of the options in ur fstab. But hey i dont judge.
If you want your HDD to automaticly mount at start-up you need to add the auto option to the line.

This is your fstab
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0 
/dev/sdb2 /media/sdb2 ntfs defaults 0 0 
/dev/sda2 /media/sda2 ntfs nls=iso8859-1,ro,users,umask=000 0 0 
/dev/sdc1 /media/sdc1 ext3 errors=remount-ro,users 0 0 

if i want sdc1 to automaticly mount i would do it like this
/dev/sdc1 /media/sdc1 ext3 auto,errors=remount-ro,users 0 0 

the same with sda2
/dev/sda2 /media/sda2 ntfs auto,nls=iso8859-1,ro,users,umask=000 0 0

these 2 drives will now automaticly mount at system start-up.
hope it helps.

---

### Post by Penguin Guy on 2010-04-18
Slownis, it looks like you've been moving/adding disks. If you're going to do stuff like that, you need to use [FONT="Courier New"]UUID[/FONT] instead of [FONT="Courier New"]/dev/sd??[/FONT].
To get the UUIDs, you'll need to run [FONT="Courier New"]sudo blkid -c /dev/null[/FONT] ([like Morbius1 said]("http://ubuntuforums.org/showthread.php?p=9139141#post9139141")).

But first, I would advise booting from the live CD, then adding labels to each partition - this makes it easier to keep track of which ones are which. Like I've done:
```

# blkid -c /dev/null
/dev/sda1: UUID="5C1886B518868E28" LABEL="**Windows**" TYPE="ntfs" 
/dev/sda5: LABEL="**boot**" UUID="6b8d5098-644c-4c56-8c6e-48e27c5a8b91" TYPE="ext4" 
/dev/sda6: LABEL="**root**" UUID="852ef378-9006-42ff-8d02-639edc154e5d" TYPE="ext4" 
/dev/sda7: LABEL="**home**" UUID="7758d068-be74-4d63-8b1c-f7eff8bcfd9c" TYPE="ext4" 
/dev/sda8: LABEL="**Arch Linux**" UUID="09de7752-4d19-4bb0-b552-4bd371e5ac07" TYPE="ext4" 

```

Then edit [FONT="Courier New"]/etc/fstab[/FONT] appropriately, here's mine to compare:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=852ef378-9006-42ff-8d02-639edc154e5d /               ext4    relatime,errors=remount-ro 0       1
UUID=6b8d5098-644c-4c56-8c6e-48e27c5a8b91 /boot           ext4    relatime        0       2
UUID=7758d068-be74-4d63-8b1c-f7eff8bcfd9c /home           ext4    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by Penguin Guy on 2010-04-18
> **Drenriza said:**
> i dont get some of the options in ur fstab. But hey i dont judge.
[COLOR="Red"]If you want your HDD to automaticly mount at start-up you need to add the auto option to the line.[/COLOR]
Actually auto means 'detect the filesystem automatically', all devices in [FONT="Courier New"]/etc/fstab[/FONT] are mounted automatically.


> **Drenriza said:**
> Not correct.

You can in the field 3'rd field add auto. this mens it auto detect the filesystem. the auto in the 4'rd field means it automaticly boot at start-up.

as noauto, in the 4'rd field means it wont automaticly boot at start-up.
Sorry, my mistake. But my point still applies - there's no point in using auto because it is implied by default.

---

### Post by Drenriza on 2010-04-18
> **Penguin Guy said:**
> Actually auto means 'detect the filesystem automatically', all devices in [FONT="Courier New"]/etc/fstab[/FONT] are mounted automatically.

Not correct.

You can in the field 3'rd field add auto. this mens it auto detect the filesystem. the auto in the 4'rd field means it automaticly boot at start-up.

as noauto, in the 4'rd field means it wont automaticly boot at start-up.

---

### Post by Morbius1 on 2010-04-18
Just in case somebody stumbles across this topic I would just like to mention something about this line in fstab:

>  /dev/sda2                                  /media/sda2     ntfs  nls=iso8859-1,ro,users,umask=000  0  0  **ro** - mounts the file system as read only
**umask=000** - mounts the files system with read / write access to everyone
**users** - allows every user to mount and unmount the file system. Why you'd want any user to unmount a partition that you're automounting at boot is perplexing. 

That exact line ( with slight variations ) is showing up all over this forum. I don't know if it's comming from some HowTo or if Pysdm is the cause of it, but Holy Frijoles. It apparently works because it keeps getting perpetuated in topic after topic. But it works despite itself not because of it.

For what it's worth, if you were to use the manual partitioning option at install time Ubuntu would have added the following line in fstab for a given NTFS partition:

> UUID=DA9056C19056A3B3 /windows/C      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1I modify this a bit, but it's a good starting place.

---

### Post by Slownis on 2010-04-18
Ya, I have no idea what all the options in fstab mean, thats why I posted in Absolute Beginner Talk.  Thanks for all the info guys.  Apart from removing the SDB line, I haven't ever manually touched it, I've only used Pysdm and Palimpsest.  Sounds like one of those utilities need some work.

The original install was with only the 30 and 40 gig hard drives (Ubuntu is on the 40 gig), and a 640 gig drive that I had to remove because it went out, and now I've replaced it, and also added a 100 gig drive.   I may have inadvertently switched the wires around in the process.

Assuming I can make it for a while with no more failures, there shouldn't be any more moving of drives.

I think I can get fstab working correctly from the info that was posted here, but what about the SMART data?  Before I was able to use Palimpsest to go in and look at the temperature of the drives, and now I can't.  Any ideas here?

---

### Post by Morbius1 on 2010-04-18
SMART has ben disabled because it does dumb things to SSD's:

[https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6](https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6)
> 
devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

  * Add 11-disable-smart-probing.patch: Disable ATA SMART probing on ATA
    disks. It causes hardware damage to a lot of SSD disks. This is a
    workaround, until a real fix in libatasmart is found. (LP: [#445852]("https://edge.launchpad.net/bugs/445852"))
 -- Martin Pitt <email address hidden>   Thu, 25 Mar 2010 18:47:35 +0100

---

### Post by Penguin Guy on 2010-04-18
> **Slownis said:**
> I think I can get fstab working correctly from the info that was posted here, but what about the SMART data?  Before I was able to use Palimpsest to go in and look at the temperature of the drives, and now I can't.  Any ideas here?
> **philinux said:**
> On 9.10 smart is currently disabled in Disk Utility due to the bad sector bug, i.e. reporting false bad sectors. Should be fixed soon I hope.

Meanwhile there's [gsmartcontrol]("apt:gsmartcontrol") available from synaptic.


Also I would strongly advise using UUIDs and to stop using pySDM (these graphical apps simplify things, but never work perfectly).

If that's all you need to know, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). If you need more information later, you can always mark it as unsolved again. Good luck.

---

### Post by QLee on 2010-04-18
[QUOTE=Slownis]Ya, I have no idea what all the options in fstab mean, thats why I posted in Absolute Beginner Talk.  Thanks for all the info guys.[/QUOTE]

It is always a good idea to investigate any advice before following it, you can read about what those options in fstab mean by entering the command, man fstab, in a terminal. That will show you the manual page and explain what the fields in fstab mean and what the defaults are. You could ask questions for anything you don't understand.

---

### Post by Drenriza on 2010-04-18
A quick review of fstab.
 
Field#1
is the filesystem you want to mount. If the entry is **none** means that the filesystem is a viratual filesystem that doesnt physical exists.
 
Field#2 
Is the mount point of the filesystem
 
Field#3
Is the format your filesystem is. Ext2, Ext3, reiserfs, ntfs e.c.t.
 
Field#4
Options you can add.
 
**async**, Read all I/O files asynchronously.
**auto**, mount automaticly. noauto dont automaticly mount the device
**dev**, allow block devices to be read from the volume
**exec**, allows programs and scripts to be run from the volume
**owner**, only the device owner can mount and umount the device
**ro**, read only
**rw**, read write
**suid**, allows the suid to be set on the files in the volume
**user**, specify a user who can mount and umount the device
 
default, defaults settings are: **rw, suid, dev, exec, auto, nouser, async**
 
In almost all the commands you can set "**no**" infront of the command. This will deny the command instead of allowing it.
 
example is: **noexec** (no programs and scripts can be run from the volume now) if you want to allow it. just write **exec** instead of **noexec**.
 
Field#5
This number is used by the dump command when backing up the filesystem.
 
options#
0 or 1
 
Field#6
Here you can define if you want the filesystem to do an fsck check. always, at crash, never.
 
0 = never do fsck
1 = do fsck at crash, no gracefull shutdown/umount
2 = always do fsck at all
 
hope this helps.

---

### Post by Morbius1 on 2010-04-18
If you go to the terminal and type **man mount** you will see that there are over 7000 options you can use is fstab. OK, that's a slight exaggeration. Not all options are relevant to each filesystem so what works on an ext3 filesystem will not work on a FAT32 or NTFS filesystem. If you try in one sitting to understand which option to use with which and which ones only work in combination with others one of two things will happen:

You will know far more than the creator of pysdm.
Or you will go mad.

My advice has always been to start slow. It's really just a set of three templates:

***STEP 1: Find out how the system sees your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

This will output , among other things the following partitions that I want to mount at boot:

/dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat"
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a" TYPE="ext3"

***STEP 2: Create mount points for your partitions to live in***

Open **Terminal**
Type **sudo mkdir /media/WinC**
Type **sudo mkdir /media/WinD**
Type [B]sudo mkdir /media/Data
[/B]
***STEP 3: Add lines to /etc/fstab/ to have these partitions mount at boot:***

/dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda6 /media/WinD vfat utf8,umask=007,gid=46 0 2
/dev/sdb6 /media/Data ext3 defaults,noatime 0 2

For the ntfs and vfat entries:

**umask=007** This will allow the owner (first digit) and group (second digit) read / write access. All others (third digit) will have no access.
**gid=46 **This is the group id and it's set to 46 (plugdev). All local login users are members of the plugdev group by default.
What's implicit is that the owner is root.

So these will mount a partition with owner = root and read / write access to all local login users.

For the ext3 entry:

It will mount a linux formatted partition with owner = root and with read / write permissions to root and read only to everyone else. Unlike windows filesystems ownership and permissions are done after it's mounted and not in fstab. For example, for a ext3 data partition:

Open **Terminal**
Type **sudo chown -R morbius:46 /media/Data**
*[COLOR=Blue]This will change ownership:group from root:root to morbius:46[/COLOR]*

OR

Open **Terminal**
Type **sudo chmod -R 0777 /media/Data**
[COLOR=Blue]*This will change permissions to allow everyone to read and write to that partition.*[/COLOR]

Or any number of combinations of those two.

*You need to be careful with the "-R" option here. If your mounting another linux OS for example you don't want to use the -R option because that will change ownership and permissions to everything within that partition. *

You are also not limited to using the /dev/sda1 type of device identifier. You could use any of these for example:

/dev/sda1
UUID=DA9056C19056A3B3
LABEL=WinXP

***Step 4: Mount them by executing the new fstab***

Open **Terminal**
Type [B]sudo mount -a
[/B]
There are a great number of different options you can use with these fstab entries depending on your particular needs. The options in the templates you see in step 3 are what happens when you allow Ubuntu to set up these non-system partitions when choosing the manual partitioning option during an install. It's a workable place to start and as your needs and experience grow you will be able to modify them to suit.

---

