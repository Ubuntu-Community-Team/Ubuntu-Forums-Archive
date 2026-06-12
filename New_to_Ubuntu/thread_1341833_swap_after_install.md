---
title: "swap after install"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-30
I did not create swap partition at the time of installing ubuntu. Now I have created a swap partition (I selected "swap" instead of "Ext4" in Partition "Type") using Disk Utility. Do I need to do anything else to ensure that Ubuntu understand it is a swap partition?

---

### Post by spongypants23 on 2009-11-30
You need to tell Ubuntu where the swap partition is. I think this is done by editing the /etc/fstab file. I don't know how this is done, though.

---

### Post by ajgreeny on 2009-11-30
Yes, spongypants23 is right, you will need to edit the /etc/fstab file as root, to do it.  Can you please post the output in terminal of ```
sudo fdisk -l
``` and then ```
sudo blkid
``` which will tell us all we need to know to put you right on this.

PS:  That's a lower case L at the end of the first command, not a figure 1.  Lot's of people get that wrong and wonder what has gone wrong.

---

### Post by Grenage on 2009-11-30
/etc/fstab:

```
/dev/hd*xx*  	swap  	swap  	defaults  	0  	0
```

Replace *xx* with drive and partition (e.g: /dev/hda4);  UUID is preferable to the name, example:

```
UUID=*e6626634-7cc2-4bfe-bc15-5c8c5d6bf721* none            swap    sw              0       0
```

Also:

```
mkswap -f /dev/hd*xx*
swapon /dev/hd*xx*
```

This command will make use of the swap immediately, requiring no reboot.

---

### Post by iRounak on 2009-11-30
The /etc/fstab file:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=9214d603-529b-485d-a523-11a23480d4fc /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0It does not contain:
/dev/hd*xx*      swap      swap      defaults      0      0
Also, please tell me how to edit the file since I am likely to run into permissions problem. Or do I have to login as root only like ajgreeny said.

---

### Post by Grenage on 2009-11-30
Ok; as **ajgreeny** said, run:

```
sudo blkid
```

You will get an output along the lines of:

```
/dev/sda1: UUID="f3d2d07c-f275-4954-bc0e-1c47c000d1e4" TYPE="ext4"
**/dev/sda5: UUID="e6626634-7cc2-4bfe-bc15-5c8c5d6bf721" TYPE="swap"**
/dev/sdb1: LABEL="archive" UUID="410ed6c9-48b6-43a0-af15-fa1062c0df04" TYPE="ext3"
```

Take the "swap" UUID and add it to your fstab.  To edit fstab via GUI:

```
gksu gedit
```

Example:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda2 during installation
UUID=9214d603-529b-485d-a523-11a23480d4fc / ext4 errors=remount-ro 0 1
**UUID=e6626634-7cc2-4bfe-bc15-5c8c5d6bf721 none swap sw 0 0**
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by hal10000 on 2009-11-30
you need to post the output of the commands ```
sudo fdisk -l
``` and ```
blkid
``` as ajgreeny stated above, otherwise nobody can help you.

---

### Post by iRounak on 2009-11-30
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2e2c2e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1974    15856123+   7  HPFS/NTFS
/dev/sda2            1975        5908    31588352   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            5908       11724    46719696   af  HFS / HFS+
Partition 3 does not end on cylinder boundary.
/dev/sda4           11725       19457    62115322+   5  Extended
/dev/sda5           11725       15459    30001356   83  Linux
/dev/sda6           15460       18559    24900718+  83  Linux
/dev/sda7           18560       19457     7213153+  82  Linux swap / Solaris

blkid
/dev/sda1: UUID="7E8843D688438B99" TYPE="ntfs" 
/dev/sda2: UUID="9214d603-529b-485d-a523-11a23480d4fc" TYPE="ext4" 
/dev/sda3: UUID="2a10d03e-cef0-3062-916c-fc0fa034eba6" LABEL="disk1s3" TYPE="hfsplus" 
/dev/sda5: LABEL="disk1s4" UUID="8c726509-60d1-4a7b-9818-9ea7e217bc3b" TYPE="ext4" 
/dev/sda6: LABEL="disk1s5" UUID="10f97e65-bdd9-4788-a285-023846ec751f" TYPE="ext4" 

There is nothing here related to sda7.
Disk Utility shows Unrecognized partition but shows type as Linux swap (0x82)

---

### Post by iRounak on 2009-11-30
my mistake...........wait

---

### Post by iRounak on 2009-11-30
Actually, though Disk Utility showed type as "Linux swap (0x82)", there was a create partition button below. I clicked it and selected Swap space. Now I was able to get UUID with sudo blkid
/dev/sda7: UUID="23534099-2ed6-40c6-a615-4fcda014e431" TYPE="swap" 
Accordingly, i edited fstab, now it looks like this:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=9214d603-529b-485d-a523-11a23480d4fc /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=23534099-2ed6-40c6-a615-4fcda014e431 none            swap  s  sw              0       0


Then I ran these commands:
 sudo mkswap -f /dev/sda7

Setting up swapspace version 1, size = 7213148 KiB
no label, UUID=e1933ca6-d0f2-43c4-b771-36936a121cd6

$ sudo swapon /dev/sda7
(no output after this command)

Is everything ok? Is there a way to verify?

---

### Post by Grenage on 2009-11-30
Using mkswap looks live it changed the UUID, the one in fstab doesn't match the mkswap listed.

To make sure, forget about swapon and mkswap for now.  Run sudo blkid once more and double-check that the UID it displays is what is in your fstab.

Then type:

```
mount -a
```

And look for any errors.

P.S: *mount -a* mounts all the things in fstab (I hate it when people don't explain what commands do!).

---

### Post by iRounak on 2009-11-30
sudo blkid
/dev/sda7: UUID="e1933ca6-d0f2-43c4-b771-36936a121cd6" TYPE="swap" 



sudo mount -a
[mntent]: line 12 in /etc/fstab is bad

changed last line in fstab to
UUID=e1933ca6-d0f2-43c4-b771-36936a121cd6 none            swap  s  sw              0       0

sudo mkswap -f /dev/sda7
/dev/sda7: Device or resource busy

---

### Post by Grenage on 2009-11-30
**Forget** about mkswap.

The fact that it was busy is promising.  Now that you have changed the UUID to match, run *mount -a* again, to check for errors

---

### Post by iRounak on 2009-11-30
please see my previous post again for the result of mount -a. i get the same error even now after reboot. Also, mkswap still shows device busy

---

### Post by Grenage on 2009-11-30
Sorry, I assumed that you hadn't run it since the change, due to the order of the post.

```
UUID=e1933ca6-d0f2-43c4-b771-36936a121cd6 none swap **s** sw 0 0
```

What is that 's' for?  You don't need to try the mkswap command any more, if it works it will change your UUID again, and fstab will be wrong.  You've already created the swap, so it's no longer needed.

---

### Post by lotharmat on 2009-11-30
> **Grenage said:**
> Sorry, I assumed that you hadn't run it since the change, due to the order of the post.

```
UUID=e1933ca6-d0f2-43c4-b771-36936a121cd6 none swap **s** sw 0 0
```

What is that 's' for?

Is that 's' for spurious?

---

### Post by Grenage on 2009-11-30
> Is that 's' for spurious?

I was thinking the same thing, lol.

---

### Post by iRounak on 2009-11-30
> Sorry, I assumed that you hadn't run it since the change, due to the order of the post.
my mistake.

I got the code and hence the "s"' from Grenage who has now edited the post (or maybe I made the mistake while copying his code and pasting it). Everything is fine now. I don't get any errors with sudo mount -a. 

Thank you everyone for the help.

---

### Post by Grenage on 2009-11-30
I only copied and pasted examples from my machine.  Regardless, I am glad it's working now.

---

### Post by iRounak on 2009-11-30
to Grenage, hope you saw my edited post

---

### Post by Grenage on 2009-11-30
Yup yup :)

---

