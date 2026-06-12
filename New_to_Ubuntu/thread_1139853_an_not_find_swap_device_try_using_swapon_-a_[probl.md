---
title: "an not find swap device try using swapon -a [problem with hibernate ]"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by me.translucent on 2009-04-27
my hibernate option not working !! well i know it's not a strange thing for ubuntu but it used to work in a fresh installation.
Right now i am using a system that i conveted to a dedicated partition from wubi .
The error messege shown is :
**can not find swap device try using swapon -a**
I tried using swapon -a too it didn't worked .
and my 
```
swap on -s 
``` output is 
```
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	1052216	0	-1

```

---

### Post by unutbu on 2009-04-27
Please post the output of 
```
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by me.translucent on 2009-04-28
```

ashu@ubuntu:~$ sudo blkid -c /dev/null
[sudo] password for ashu: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0101" TYPE="vfat" 
/dev/sda2: UUID="088C17A88C178F76" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="5252B3D952B3BFD1" LABEL="OS" TYPE="ntfs" 
/dev/sda6: UUID="7949253F727BC349" TYPE="ntfs" 
/dev/sda7: UUID="c9825710-bbaa-4a7d-85d9-6a4dc0d124c6" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="3a890813-e156-4b4d-9b9a-9de37650b573" 
ashu@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=c9825710-bbaa-4a7d-85d9-6a4dc0d124c6

```

---

### Post by unutbu on 2009-04-28
The UUID listed in /etc/initramfs-tools/conf.d/resume
tells your system which partition to read when trying to resume.
It should point to a swap partition. In your case, it should point to sda8, not sda7.

Therefore, we need to edit /etc/initramfs-tools/conf.d/resume.

Open a terminal, and type```


gksu gedit /etc/initramfs-tools/conf.d/resume
```

Change```


c9825710-bbaa-4a7d-85d9-6a4dc0d124c6
```

to
```

3a890813-e156-4b4d-9b9a-9de37650b573
```

Save and exit gedit. Then try hibernating again.

---

### Post by logos34 on 2009-04-28
> **unutbu said:**
> The UUID listed in /etc/initramfs-tools/conf.d/resume
tells your system which partition to read when trying to resume.
It should point to a swap partition. 

Mine doesn't match what blkid and ls -l /dev/disk/by-uuid, but it still suspends and hibernates fine.  Why?

> $ sudo blkid
/dev/sda5: LABEL="Home" UUID="92e1dc9c-0758-408a-873b-48ba419e8e88" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Root" UUID="d77656b5-aa1c-4375-8bfa-b517cebff023" TYPE="ext3" 
**/dev/sda7: TYPE="swap" UUID="d9ed324a-d196-4b57-ba49-6cc0b04e67bc"** 
/dev/sda2: UUID="b16b0886-50a6-45c6-9d57-651738b27784" SEC_TYPE="ext2" TYPE="ext3" LABEL="Grub" 

$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=[COLOR="Red"]4264a7bc-a05a-432f-93bb-8c2bb0709ee7[/COLOR]




---

### Post by unutbu on 2009-04-28
Thanks for the information, logos34. 
It appears my advice is wrong -- or perhaps obsolete.

My information came from this post,
[http://ubuntuforums.org/showpost.php?p=5168992&postcount=5](http://ubuntuforums.org/showpost.php?p=5168992&postcount=5)
which is dated 2008-06-12.

Your post spurred me to do a bit more research. 
The script /etc/acpi/hibernate.sh uses /etc/initramfs-tools/conf.d/resume.
/etc/acpi/hibernate.sh is part of acpi-support package.

It appears there are two independent ways to suspend/hibernate under Ubuntu: acpi-support and pm-utils. According to 
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg563331.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg563331.html),
it sounds like under Debian (and maybe Ubuntu too?) acpi-support has been deprecated, and pm-utils is now used by default.

Sorry me.translucent, my previous suggestion probably won't work for you, unless you use Hardy or a prior release.

---

### Post by unutbu on 2009-04-28
me.translucent, here is a report from a person who uses 

/etc/acpi/sleep.sh (in Jaunty) to suspend: See  [http://ubuntuforums.org/showpost.php?p=7168602&postcount=3](http://ubuntuforums.org/showpost.php?p=7168602&postcount=3)

---

### Post by me.translucent on 2009-04-29
okay should i change 
```
  /etc/initramfs-tools/conf.d/resume
```
back to what it was before ?

---

### Post by unutbu on 2009-04-29
I would leave   /etc/initramfs-tools/conf.d/resume corrected as I suggested in post #4.

/etc/initramfs-tools/conf.d/resume is not used by pm-utils, and pm-utils is the default method for suspend/hibernate on Ubuntu now. However, it is used by acpi-support, so if you'd like to try suspend/hibernate using acpi-support, you'll need to have /etc/initramfs-tools/conf.d/resume set correctly.

If you'd like to try acpi-support's method to suspend/hibernate, try running
```

sudo /etc/acpi/sleep.sh sleep        # to suspend

sudo /etc/acpi/hibernate.sh force    # to hibernate
```

If it works, we can work on setting these commands as the default way your machine suspends and hibernates. (I'm not exactly sure how to do that, but I think we can figure that out).

---

### Post by me.translucent on 2009-04-30
dude .. it's not working .. niether the command line nor the GUI.:(

---

### Post by unutbu on 2009-04-30
How about try this then:
[http://ubuntuforums.org/showthread.php?t=471855&highlight=shutdown](http://ubuntuforums.org/showthread.php?t=471855&highlight=shutdown)

---

### Post by me.translucent on 2009-05-04
the same problem .. i have attached the screenshot .. which configration file defines the swap partition for hibernate ?and yeah some thing is wrong with my grub too it keeps showing so many options that don't work ..may be the two problems are related .

---

### Post by unutbu on 2009-05-04
Hm. I don't know. Could you post
```

cat /etc/fstab
free
``` 
Not sure this is related, but, how much RAM do you have?

---

### Post by me.translucent on 2009-05-04
*a *

---

### Post by me.translucent on 2009-05-04
```
ashu@ubuntu:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda7
UUID=c9825710-bbaa-4a7d-85d9-6a4dc0d124c6     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda6
UUID=7949253F727BC349       /media/drv0       ntfs-3g         defaults      0   0
# /dev/sda5
UUID=7949253F727BC349       /media/OS	ntfs-3g         user      0   0
/media/drv0/Music	/home/ashu/Music	none	bind	

# /dev/sda8
UUID=3a890813-e156-4b4d-9b9a-9de37650b573      none            swap        sw          0   0

ashu@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       2071312    1441560     629752          0     111104     698052
-/+ buffers/cache:     632404    1438908
Swap:      1052216          0    1052216


```

---

### Post by me.translucent on 2009-05-04
And yeah i was concerned about the ram thing too .. i have 2 gb of ram while only a single gb of swap partion.

---

### Post by unutbu on 2009-05-04
Okay, I think I see a problem: You have about 2+ GiB of RAM, but only 1GiB of swap. When you suspend, the current state of the machine (in RAM) is flushed to your swap. But that can not be done if RAM is bigger than swap. 

In order to suspend, you need at least as much swap space as RAM.

I can't say for sure, but this might be the source of all your problems. 

Depending on your current setup, you could either use GParted to expand sda8, or perhaps, delete sda8, expand a neighboring partition, and use a swap file instead of a swap partition. 

If you'd like some help with this, please post
```

sudo fdisk -l
```

---

### Post by me.translucent on 2009-05-04
i am posting the output but as all the error message indicates the system is not able to find the swap space,the question of having a big enough partition comes only after locating a swap!! 
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3            1317       30401   233625262+   5  Extended
/dev/sda5            1317        3875    20555136    7  HPFS/NTFS
/dev/sda6            3905       28361   196450821    7  HPFS/NTFS
/dev/sda7           28362       30270    15334011   83  Linux
/dev/sda8           30271       30401     1052226   82  Linux swap /Solaris

```

---

### Post by logos34 on 2009-05-04
what does

> sudo blkid 

show?

> **unutbu said:**
> 
In order to suspend, you need at least as much swap space as RAM.

I can't say for sure, but this might be the source of all your problems. 
[/CODE]

+1

But it should be able to find and use swap otherwise, so there's some other problem.

For making a swap *file*:

[https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file](https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file)

---

### Post by logos34 on 2009-05-04
[delete-duplicate]

---

### Post by unutbu on 2009-05-04
I am guessing (or rather, hoping!) that the reason why uswsusp was complaining it could not find an active swap partition is because it ignores swap partitions which are too small.

Anyway, after we expand the swap partition, we should go back to the beginning and try Ubuntu's default suspend/hibernate method. You may not need uswsusp at all.

Currently, your swap space is 1052216 KiB. We need to expand it to at least 2071312 KiB.
The difference is 1019096 KiB ~= 1044 MB.

To expand sda8:

First, a note of warning: Whatever you do, you do not stop GParted once it has begun moving the partitions. If you cancel the operation midway, or if the machine loses power, then your Linux partition will become corrupted, and most likely you will lose data and have to reinstall Ubuntu. Because of this risk, many advise that you backup your data before doing any move/resize operations. 

If you do not have a backup of your data, I'd recommend doing that before you try expanding sda8.

When you are ready to resize sda8:

Boot from a LiveCD. Select System>Admin>Partition Editor to launch GParted.
Click to select sda7 (The Linux partition to the left of the swap partition).
Click Resize.
Shrink sda7 (on the right-hand side) by 1044 MB.
Click on sda8 (the swap partition)
Click Resize.
Expand sda8 (to the left) to fill all free space.
Check in the main window that GParted reports the new size of sda8 is at least 1.98 GiB (slightly bigger than 2071312 KiB).
Click Apply.

---

### Post by me.translucent on 2009-05-08
yupp did it .. but of no use .. still swap not found :(

---

### Post by fullgospel on 2009-11-06
Hey,

Im guessing you have an NVIDIA graphic card. the 173 or 180 driver update got me the same problem, uninstall it, it works, install it, it doesnt anymore...dunn why

---

### Post by me.translucent on 2009-11-06
okay i'll try it tommorow as a last resort ..otherwise i'll probably install a fresh copy

---

