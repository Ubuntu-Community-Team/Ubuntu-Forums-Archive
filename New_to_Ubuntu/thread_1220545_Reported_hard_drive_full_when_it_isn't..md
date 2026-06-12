---
title: "Reported hard drive full when it isn't."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by iamed18 on 2009-07-22
Hello Grand Community

I am here as a simple man, needing assistance.

I just reinstalled Ubuntu Desktop 9.04 on my machine that I use as a server, and it now finds that my 1.5 TB hard drive is 100% full when it only has ~~1300gb of data on it.  I know that the drive isn't full because before I formatted the OS drive (a 120gb HDD), the Ubuntu installing prior to this one said that there was ~~100gb free.

I don't know if this is a setting of if I need to reformat the entire drive (which I'm very against, as it is 1340gb of data that would be hard to find a back up location for at the moment).

Any ideas? :confused:

---

### Post by LowSky on 2009-07-22
sounds like you screwed up and have been placing data onto your OS drive, which is now full

---

### Post by Durden on 2009-07-22
Type: "df -h" at the command prompt and post the results here please.

---

### Post by iamed18 on 2009-07-22
> **Durden said:**
> Type: "df -h" at the command prompt and post the results here please.
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             110G  2.9G  101G   3% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  296K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  148K  502M   1% /dev
tmpfs                 502M  704K  501M   1% /dev/shm
lrm                   502M  2.2M  500M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1             1.4T  1.3T     0 100% /storage

```

---

### Post by iamed18 on 2009-07-22
> **LowSky said:**
> sounds like you screwed up and have been placing data onto your OS drive, which is now full


I checked that, and it isn't that because firstly, I don't use the 1.5T for an OS, and the other drive was JUST formatted and placed in this machine.

---

### Post by Durden on 2009-07-22
Well, according to df your /storage partition is full. BTW, just because you bought a 1.5T drive doesn't mean it is one. A lot of space gets used by the filesystem itself which is why it's sitting at 1.3T and full.

---

### Post by iamed18 on 2009-07-22
> **Durden said:**
> Well, according to df your /storage partition is full. BTW, just because you bought a 1.5T drive doesn't mean it is one. A lot of space gets used by the filesystem itself which is why it's sitting at 1.3T and full.

I realize that you don't get the full "1.5T" that it says on the box, but the thing is, with my previous OS (8.04), I still had about 100GB free, and now that's gone.  Very literally 0 Bytes free.  This doesn't seem right.

---

### Post by Rubicon_82 on 2009-07-23
Hi,

The output of 'df -h' is showing your disk with a capacity of 1.4 TiB (i.e. 1.4 * 2^40 bytes), whereas the manufacturer probably claimed the drive has a capacity of 1.5 TB (i.e. 1.5 * 10^12 bytes).  1.5 TB is approximately 1.36 TiB.

Regarding the drive showing 100% capacity when it only contains 1.3 TiB of data:

What has the drive been formatted as?  Ext3 (and possibly ext4) reserves a portion of the drive for use by the root user, typically 5%.  This is useful for small drives containing the OS, as it allows things such as syslogd to continue functioning when the drive appears full to the user.  For large drives used only for user-level data storage, reserving 5% of the drive for root simply wastes space.  If your partition is formatted as ext3, try running the following command to list the properties of the volume.
```

sudo tune2fs -l /dev/sda1

```

 In the output, look for the *Reserved block count* field.  If it is non-zero, you can reduce this by using the *-m* or *-r* flags.  For more information, see
```

man tune2fs

```

---

### Post by mapes12 on 2009-07-23
Hi 

Check this out:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

It worked for me when I had an unexplained full HDD.

---

### Post by iamed18 on 2009-07-29
> **Rubicon_82 said:**
> Hi,

The output of 'df -h' is showing your disk with a capacity of 1.4 TiB (i.e. 1.4 * 2^40 bytes), whereas the manufacturer probably claimed the drive has a capacity of 1.5 TB (i.e. 1.5 * 10^12 bytes).  1.5 TB is approximately 1.36 TiB.

Regarding the drive showing 100% capacity when it only contains 1.3 TiB of data:

What has the drive been formatted as?  Ext3 (and possibly ext4) reserves a portion of the drive for use by the root user, typically 5%.  This is useful for small drives containing the OS, as it allows things such as syslogd to continue functioning when the drive appears full to the user.  For large drives used only for user-level data storage, reserving 5% of the drive for root simply wastes space.  If your partition is formatted as ext3, try running the following command to list the properties of the volume.
```

sudo tune2fs -l /dev/sda1

``` In the output, look for the *Reserved block count* field.  If it is non-zero, you can reduce this by using the *-m* or *-r* flags.  For more information, see
```

man tune2fs

```

Well, I would love to believe that this is the issue, however, I can not.

I backed up all of the data on the drive (on several other drives) and I loaded up gParted to format the drive.  And lo, it finds not a 1.5TB drive, but a 500GiB one.

This opens up an entire new bottle of issues, from which I have no idea where to start except than to take the drive out and check the jumpers...which I'm pretty sure shouldn't make any difference.

---

### Post by llamabr on 2009-07-29
I wouldn't bother with jumpers.  Navigate to that /storage directory in terminal, and look around.  You might have log files filling it up, hidden directories, a .Trash/ directory, or others.

How much do you believe should be there?

---

### Post by jerome1232 on 2009-07-29
It almost sounds like something is wrong with the partition table to me. I remember stumbling on a similar thread with a solution but can't find it for the life of me.

---

### Post by jrox717 on 2009-07-30
I am using Boabab, which is described as a "Disk Usage Analyzer" and it shows the size of directories by level and percentage of HD used... You may want to take a look (though this is nothing that can't be done manually).

---

### Post by iamed18 on 2009-07-31
The following is what I did.

1. Backed up all of my data.
2. used fdisk to delete the partition, and to recreate it.
3. used mkfs.ext4 to create a new filesystem
4. mounted, changed permissions, and df -h

Output confirmed that the drive was 1.5T with 128MiB in use.  I have since begun collecting the files from their backup locations and everything is smooth thus far.

Thanks for the help, but I guess I just gave up and formatted.

---

