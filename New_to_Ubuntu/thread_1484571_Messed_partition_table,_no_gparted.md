---
title: "Messed partition table, no gparted"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by maurolust on 2010-05-15
Hi everyone.

I just installed Lynx, but somehow got it wrong in the partition editing phase, later I tried intalling it on autopilot (preserving older filesystems). Now I have one partition for the Lynx, two swap spaces, one unmounted partition with a failed lynx installation, my old /home partition (unmounted), a windows partition (running fine), and  a standalone bootloader partition (16M unmounted, and the bootloader is probably not installed there anyway either).

What I would like to do, so I can have a decent usage of my disk estate without reinstalling everything is:

[LIST=1]
[*]Mount my old /home partition as, well... /home
[*]Format my old ubuntu partition and merge it with that
[*]Have only one swap partition (2MB would be more than enough, right?)[/LIST]

Leave Grub where it is, if it's in my new Ubuntu partition, end that standalone partition. If it's installed in that standalone partition, my work is done. The problem is if it is in the partition I want to clear, then I don't know what to do.

Now, what is making me crazy: I can't use Parted for that! It is installed on my system, but I can't run it. It's not under system>administration and I'm afraid I'll make more of a mess if run it in command line mode. I can't run it from sbin either, even after I sudo su.

Here is what it looks like currently
```
Model: ATA Hitachi HTS54168 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs
 2      1574MB  25.9GB  24.3GB  primary   ntfs
 4      25.9GB  80.0GB  54.1GB  extended
 7      25.9GB  36.2GB  10.2GB  logical   ext3            boot
 8      36.2GB  58.5GB  22.4GB  logical   ext3
 9      58.5GB  76.5GB  18.0GB  logical   ext4
10      76.5GB  77.4GB  832MB   logical   linux-swap(v1)
 6      77.4GB  77.4GB  16.8MB  logical   ext3
 5      77.4GB  80.0GB  2656MB  logical   linux-swap(v1)

```

The boot flag kind of tells me the bootloader is installed in the same partition as my failed lynx installation, is that right?

My new instalation is partition 9, my old home is 8 and the failed installation is 7.

---

### Post by ratcheer on 2010-05-15
The easiest thing to do would be to run Gparted from a Live CD.

Tim

---

### Post by ranch hand on 2010-05-15
> **maurolust said:**
> Hi everyone.

I just installed Lynx, but somehow got it wrong in the partition editing phase, later I tried intalling it on autopilot (preserving older filesystems). Now I have one partition for the Lynx, two swap spaces, one unmounted partition with a failed lynx installation, my old /home partition (unmounted), a windows partition (running fine), and  a standalone bootloader partition (16M unmounted, and the bootloader is probably not installed there anyway either).

What I would like to do, so I can have a decent usage of my disk estate without reinstalling everything is:

[LIST=1]
[*]Mount my old /home partition as, well... /home
[*]Format my old ubuntu partition and merge it with that
[*]Have only one swap partition (2MB would be more than enough, right?)
[/LIST]

Leave Grub where it is, if it's in my new Ubuntu partition, end that standalone partition. If it's installed in that standalone partition, my work is done. The problem is if it is in the partition I want to clear, then I don't know what to do.

Now, what is making me crazy: I can't use Parted for that! It is installed on my system, but I can't run it. It's not under system>administration and I'm afraid I'll make more of a mess if run it in command line mode. I can't run it from sbin either, even after I sudo su.

Here is what it looks like currently
```
Model: ATA Hitachi HTS54168 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1574MB  1573MB  primary   ntfs
 2      1574MB  25.9GB  24.3GB  primary   ntfs
 4      25.9GB  80.0GB  54.1GB  extended
 7      25.9GB  36.2GB  10.2GB  logical   ext3            boot
 8      36.2GB  58.5GB  22.4GB  logical   ext3
 9      58.5GB  76.5GB  18.0GB  logical   ext4
10      76.5GB  77.4GB  832MB   logical   linux-swap(v1)
 6      77.4GB  77.4GB  16.8MB  logical   ext3
 5      77.4GB  80.0GB  2656MB  logical   linux-swap(v1)

```The boot flag kind of tells me the bootloader is installed in the same partition as my failed lynx installation, is that right?

My new instalation is partition 9, my old home is 8 and the failed installation is 7.
It sounds like you had a bad day.

Gparted should not really be used from an OS on the drive being partitioned.  You will probably get away with it most of the time but then there will be the bad ones.

Gparted is standard on all Live CDs so this should not be a problem.  Do it from there.  It is, as in your installation, located at System>Administration>Gparted.

I would do away with every thing but the old /home partition and the MS install and create one extended partition in that now empty space.

Put your swap at the end of that and create a partition for / at the beginning of that space..

When you install use the "manual" option and then you can tell the installer where to put things as far as / and /home go.

Make sure that grub is not installed anywhere but on the MBR.  There was a bug that recommended installing it everywhere if you were not sure.  Just on the MBR, which is identified as your drive.  In other words /dev/sda and nowhere else.

You should be fine.

---

### Post by warfacegod on 2010-05-15
I noticed, in the Thread's title, you said Gparted but, in the body of the post, you refer to Parted. They aren't quite the same thing.

Just to be certain, open a Terminal enter:

```
sudo apt-get install gparted
```

If it turns out that it is indeed installed, right click your menu button and select "Edit Menus".

From there, in the left hand pane, highlight Administration then, in the right hand pane, put a check next to Gparted.

If you accidentally frag GRUB2, here's a link to help you reinstall it: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by maurolust on 2010-05-16
Thank you all for your replies. They were all useful, but I don't think I want to go through installation again. That's manly because my last atempt to install with manual partition editing has failed, meaning I'm not getting something. Automatic installation works, but does not mount a separate /home partition.
I only want to clear the failed partition (but I'm afraid Grub may be installed there) and put my old data at mount point /home . I did mount it successfully, but not at my desired mount point.

Oh, and put the swap at the end of the extended partition. Maybe I should leave some unallocated space between / and /home to allow for expanding / for extra software (as suggested by [oneandoneis2]("http://linux.oneandoneis2.org/starting.htm")). 

Is there no easy way to verify whether grub is really installed in the MBR? 

What about the BOOT flag? Should it be on every bootable partition or just the default? If so, why does windows start just fine even though it has no BOOT flag on it?

---

### Post by warfacegod on 2010-05-16
It probably didn't use the partition you set up for your Home folder because you forgot to mark it as /home when you setup your partition scheme just like you had to set your OS partition as / (root). I thinks its step 4? in the manual installation process.

---

