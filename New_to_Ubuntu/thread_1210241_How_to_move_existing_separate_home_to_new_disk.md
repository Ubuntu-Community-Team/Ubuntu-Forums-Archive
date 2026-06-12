---
title: "How to move existing separate /home to new disk?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by RobHK on 2009-07-11
I have /home on a separate partition but want to move it to a different disk, as I want to expand it and don't have enough space where it is now.

Most of what I have googled refers to creating a new partition for /home when it is currently on the same partition as /. It's quite complicated, but I suspect that what I need to do is much simpler.

I'm OK for copying the existing partition, and for expanding it. What I don't know is how to get the setup to address the new partition as /home.

TIA for any help.

---

### Post by drs305 on 2009-07-11
If you already know how to copy and setup your new partition, all you have to do to get the system to recognize it is to edit your fstab file, which tells the system where things are during boot.

```

sudo cp /etc/fstab /etc/fstab.bak  # Make a backup
gksudo gedit /etc/fstab  # Open fstab for editing

```

Your /home entry should look like this. Of course change the UUID ("sudo blkid" will give you the info, or you can use a label):
> 
UUID=87883h-977h-98he838-889-34  /home  ext3  nodev,nosuid 0 2


Here is a good reference. 
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> If you already know how to copy and setup your new partition, all you have to do to get the system to recognize it is to edit your fstab file, which tells the system where things are during boot.

```

sudo cp /etc/fstab /etc/fstab.bak  # Make a backup
gksudo gedit /etc/fstab  # Open fstab for editing

```

Your /home entry should look like this. Of course change the UUID ("sudo blkid" will give you the info, or you can use a label):


Here is a good reference. 
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")


Thanks. I ran blkid but there is no reference to /home in it.

```
/dev/sda1: UUID="ECA8DD64A8DD2DB8" LABEL="C System" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="ad20bc59-8888-46c0-a6b7-4eb457946251" 
/dev/sda6: UUID="88d73296-7fa0-46cd-8383-c5ce2442d7ae" TYPE="ext3" 
/dev/sda7: UUID="abaa01a6-7a2b-43fc-87cb-ebc79619cccf" TYPE="ext3" 
/dev/sdb1: UUID="10E14D6C55AA45A3" LABEL="D Documents" TYPE="ntfs" 
/dev/sdb5: UUID="44D46A4FD46A4372" LABEL="Mail" TYPE="ntfs" 
/dev/sdb6: UUID="52f512a7-79d1-49b3-96a1-4d1a269fff0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="0d44588d-3676-4fb8-92b2-fb09f270d4e6" TYPE="ext2" 
/dev/sdb8: UUID="9316cc2e-4619-4e59-a5fe-d9a991e3b28f" TYPE="ext2" 
/dev/sdb9: UUID="86ac4b6f-7b27-4e22-9e98-bf4c4333d929" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb10: UUID="aa979198-3e59-4293-a888-e16a95cc52b8" SEC_TYPE="ext2" TYPE="ext3"
```

My current /home is sda7. / is sda6. The stuff on the sdb drive is other Linux istallations that i'll probably zap.

I already saw psychocats, but I found it too complicated. It assumes you have /home on the same partition as / so it's covering a lot more than what I need to do. 

Do I need to add this to the fstab (and delte the sda7 line)?

```
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

Substituting sda3 with the correct partition, of course.

---

### Post by drs305 on 2009-07-11
> **RobHK said:**
> 

Substituting sda3 with the correct partition, of course.

Yes, just determine which partition is now your new /home partition and use that partition's UUID. 

If you like, you can also label that partition so that you *can* see it with the "blkid" command.

To label an ext3 partition, changing "sdXX" to the correct partition (I've used the term "home" for the label but you can use almost anything:
```
sudo tune2fs -L home /dev/sdXX
```

You mentioned deleting the "sda7" line - if that is your current /home and it is listed in fstab all you need to do is change the "/dev/sda7" reference to the new "sdaX" home partition, or preferably use the UUID or a label in fstab. If you aren't sure, just post your fstab and tell us what the new /home partition is.

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> Yes, just determine which partition is now your new /home partition and use that partition's UUID. 

If you like, you can also label that partition so that you *can* see it with the "blkid" command.

To label an ext3 partition, changing "sdXX" to the correct partition (I've used the term "home" for the label but you can use almost anything:
```
sudo tune2fs -L home /dev/sdXX
```

You mentioned deleting the "sda7" line - if that is your current /home and it is listed in fstab all you need to do is change the "/dev/sda7" reference to the new "sdaX" home partition, or preferably use the UUID or a label in fstab. If you aren't sure, just post your fstab and tell us what the new /home partition is.

The UUID is just the bit between quotes after "UUID =", is it? (This is new stuff to me. I haven't a clue what it actually means.)

I think I'll post the fstab after I've copied the partition. It won't be right away though. Probably later today, though it might not be till tomorrow.

Thanks for your advice.

---

### Post by drs305 on 2009-07-11
> **RobHK said:**
> The UUID is just the bit between quotes after "UUID =", is it? (This is new stuff to me. I haven't a clue what it actually means.)

I think I'll post the fstab after I've copied the partition. It won't be right away though. Probably later today, though it might not be till tomorrow.

Thanks for your advice.

Yes, the UUID is the alpha-numeric listing. For example, if the /home partition was sda7, with this as the result of the blkid command:
> /dev/sdb7: UUID="0d44588d-3676-4fb8-92b2-fb09f270d4e6" TYPE="ext2" 

the fstab entry would be:
> 
UUID=0d44588d-3676-4fb8-92b2-fb09f270d4e6 /home ext3 nodev,nosuid 0 2 

Ubuntu went to UUIDs because they are specific to a partition and don't change. Previously the fstab entries were listed as "sdXX", such as "sda5". The problem is that sometimes these designations changed - sda5 would become sdb5, which of course caused problems. The designations changed due to the mounting sequence - with UUIDs (or labels) the order of mounting doesn't matter.

If you label your new partition (example "home"), you can also make your fstab entry:
> 
LABEL=home /home ext3 nodev,nosuid 0 2 


---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> Yes, the UUID is the alpha-numeric listing. For example, if the /home partition was sda7, with this as the result of the blkid command:

the fstab entry would be:


Ubuntu went to UUIDs because they are specific to a partition and don't change. Previously the fstab entries were listed as "sdXX", such as "sda5". The problem is that sometimes these designations changed - sda5 would become sdb5, which of course caused problems. The designations changed due to the mounting sequence - with UUIDs (or labels) the order of mounting doesn't matter.

If you label your new partition (example "home"), you can also make your fstab entry:

Hi again.

I've copied /home to the second drive, but I'm still using the original /home. Partition Editor identifies it as sdb6. (I'm a bit puzzled here, because Partition Editor in Ubuntu identifies the drives as sda.sdb and sdc (external USB drive), but when I used Partition Magic to copy the /home partition the drives were identified as hda, hdb and sda respectively. The internal drives are IDE. I think the external one is SATA.)

This is my fstab

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=88d73296-7fa0-46cd-8383-c5ce2442d7ae /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=abaa01a6-7a2b-43fc-87cb-ebc79619cccf /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=ad20bc59-8888-46c0-a6b7-4eb457946251 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hda2    /media/windows vfat  iocharset=utf8,umask=000  0    0

```

As you see my first drive is identified here as hda. Partition Editor says that sda1 is my XP system partition (primary) and that sda2 is the extended partition on which are 3 logical drives containing /(sda6), /home (sda7) and /swap(sda5).

---

### Post by drs305 on 2009-07-11
> **RobHK said:**
> (I'm a bit puzzled here, because Partition Editor in Ubuntu identifies the drives as sda.sdb and sdc (external USB drive), but when I used Partition Magic to copy the /home partition the drives were identified as hda, hdb and sda respectively. The internal drives are IDE. I think the external one is SATA.)

That is the way linux/ubuntu used to describe the drives as well (hda, sda). A year or so ago the hda/sda convention was dropped and they are now all "sd"XX.

All you should have to do is replace the following area in your fstab file with the UUID of your new /home location. It would actually be better to *copy* the new entry and put a comment symbol (#) in front of the old one so you can revert if necessary. So your new fstab entries would look like the following, with the correct UUID for you new /home in the uncommented entry. The defaults you have are a bit different that what I posted earlier but if what you have works and you are happy with them then leave them alone.

One other thing. If you get error messages on boot about $HOME not being owned by you or .dmrc permission errors, refer to this thread I created about how to fix that issue:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267") or the wiki [https://help.ubuntu.com/community/dmrcErrors]("https://help.ubuntu.com/community/dmrcErrors")

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> Yes, the UUID is the alpha-numeric listing. For example, if the /home partition was sda7, with this as the result of the blkid command:

the fstab entry would be:


Ubuntu went to UUIDs because they are specific to a partition and don't change. Previously the fstab entries were listed as "sdXX", such as "sda5". The problem is that sometimes these designations changed - sda5 would become sdb5, which of course caused problems. The designations changed due to the mounting sequence - with UUIDs (or labels) the order of mounting doesn't matter.

If you label your new partition (example "home"), you can also make your fstab entry:

I ran blkid to find the UUID of my new /home (sdb6). In fstab, I copied this over the UUID of my old /home. I rebooted and saved a marker file to the desktop. This marker file is in my old /home, so it appears I am not booting into my new /home.

blkid returns:
```
/dev/sda1: UUID="ECA8DD64A8DD2DB8" LABEL="C System" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="ad20bc59-8888-46c0-a6b7-4eb457946251" 
/dev/sda6: UUID="88d73296-7fa0-46cd-8383-c5ce2442d7ae" TYPE="ext3" 
/dev/sda7: UUID="abaa01a6-7a2b-43fc-87cb-ebc79619cccf" TYPE="ext3" 
/dev/sdb1: UUID="10E14D6C55AA45A3" LABEL="D Documents" TYPE="ntfs" 
/dev/sdb5: UUID="44D46A4FD46A4372" LABEL="Mail" TYPE="ntfs" 
/dev/sdb6: UUID="abaa01a6-7a2b-43fc-87cb-ebc79619cccf" SEC_TYPE="ext2" TYPE="ext3" 

```

My present fstab:```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=88d73296-7fa0-46cd-8383-c5ce2442d7ae /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation (moved to sdb6)
UUID=abaa01a6-7a2b-43fc-87cb-ebc79619cccf /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=ad20bc59-8888-46c0-a6b7-4eb457946251 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hda2    /media/windows vfat  iocharset=utf8,umask=000  0    0

```

---

### Post by drs305 on 2009-07-11
RobHK,

The problem relates to the fact that you cloned your /home partition. Since you cloned it, it also has the same UUID. You need to give sdb6 a unique UUID. The easiest way to do this is to run:
```

sudo umount /dev/sdb6
sudo tune2fs -U random /dev/sdb6

```

Then see what the new UUID for sdb6 is and insert that into fstab.

You can also assign a specific UUID of your choosing if you really want to. Look at the "man tune2fs" page if you are interested.

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> RobHK,

The problem relates to the fact that you cloned your /home partition. Since you cloned it, it also has the same UUID. You need to give sdb6 a unique UUID. The easiest way to do this is to run:
```

sudo umount /dev/sdb6
sudo tune2fs -U random /dev/sdb6

```

Then see what the new UUID for sdb6 is and insert that into fstab.

You can also assign a specific UUID of your choosing if you really want to. Look at the "man tune2fs" page if you are interested.

It didn't work. Here is the error message:
```
tune2fs -U random /dev/sdb6
tune2fs 1.41.4 (27-Jan-2009)
tune2fs: Permission denied while trying to open /dev/sdb6
Couldn't find valid filesystem superblock.

```

---

### Post by drs305 on 2009-07-11
> **RobHK said:**
> It didn't work. Here is the error message:
```
tune2fs -U random /dev/sdb6
tune2fs 1.41.4 (27-Jan-2009)
tune2fs: Permission denied while trying to open /dev/sdb6
Couldn't find valid filesystem superblock.

```

The command has to be run as root, you most likely forgot the "sudo".
```

sudo tune2fs -U random /dev/sdb6

```

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> The command has to be run as root, you most likely forgot the "sudo".
```

sudo tune2fs -U random /dev/sdb6

```

No, I didn't forget the sudo. I'd already run it twice. The sudo wasn't required again.

But the good news is I cracked it. I decided to look in gparted and see if it told me the UUID. It did, and it wasn't the old one, as returned by blkid. I copied the UUID given in gparted, and it worked. I'm now running in my new home partition.

Thanks very much for your help.

---

### Post by LewRockwell on 2009-07-11
glad to hear you've got it done successfully and thanks for working through it with us here so others can benefit from our experiences!

.

---

### Post by drs305 on 2009-07-11
RobHK,

Congrats on figuring out the new blkid. If the "sudo blkid" is still returning an incorrect UUID, would you mind trying these two commands to see if the correct UUID is displayed?

I often, although not in this case, use the command below to prevent getting a cached blkid return.  It may or may not have mattered in this case. 
```
sudo blkid -c /dev/null
```

The other way, and this is the one listed in the fstab comments themselves, is to run:
```
sudo vol_id --uuid /dev/sd**b6**
```

If the old command doesn't work but either of the other two does, would you please post the results? As you discovered, having the current UUID is crucial for getting things to run correctly. Thanks.

---

### Post by RobHK on 2009-07-11
> **drs305 said:**
> RobHK,

Congrats on figuring out the new blkid. If the "sudo blkid" is still returning an incorrect UUID, would you mind trying these two commands to see if the correct UUID is displayed?

I often, although not in this case, use the command below to prevent getting a cached blkid return.  It may or may not have mattered in this case. 
```
sudo blkid -c /dev/null
```

The other way, and this is the one listed in the fstab comments themselves, is to run:
```
sudo vol_id --uuid /dev/sd**b6**
```

If the old command doesn't work but either of the other two does, would you please post the results? As you discovered, having the current UUID is crucial for getting things to run correctly. Thanks.

Both these work, but then so does blkid now.

```
sudo vol_id --uuid /dev/sd**b6**
``` didn't work before (i.e. when the old /home partition was still loading).

---

### Post by RobHK on 2009-10-04
> **drs305 said:**
> RobHK,

The problem relates to the fact that you cloned your /home partition. Since you cloned it, it also has the same UUID. You need to give sdb6 a unique UUID. The easiest way to do this is to run:
```

sudo umount /dev/sdb6
sudo tune2fs -U random /dev/sdb6

```

Then see what the new UUID for sdb6 is and insert that into fstab.

You can also assign a specific UUID of your choosing if you really want to. Look at the "man tune2fs" page if you are interested.

I've just done the same operation again, and it's as simple as pie! You don't need any of the stuff we messed about with. I just copied the partition to the other drive, and then deleted the original partition. Done. Sorted. 

Reboot, and the cloned partition (presumably because it has the same UUID as the original partition) loads automagically.:)

---

### Post by drs305 on 2009-10-04
> **RobHK said:**
> I've just done the same operation again, and it's as simple as pie! You don't need any of the stuff we messed about with. I just copied the partition to the other drive, and then deleted the original partition. Done. Sorted. 

Reboot, and the cloned partition (presumably because it has the same UUID as the original partition) loads automagically.:)

That's correct. The only reason you would take those steps is if you ended up with two partitions with the same UUID. If you delete one of them (the original) the problem ceases to exist!

Happy Ubuntu-ing.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

