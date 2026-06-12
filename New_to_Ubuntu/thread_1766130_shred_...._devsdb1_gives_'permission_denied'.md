---
title: "shred .... /dev/sdb1 gives 'permission denied'"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by merbce on 2011-05-24
I tried this  to wipe everything on an external (USB) HDD:
shred -u -n 2 /dev/sdb1

All I got was:  /dev/sdb1: failed to open for writing: Permission denied

Do  I need to set Administrator privileges? I am the only user.
Prior to trying shred, I formatted the volume as Ext4 after trying Eraser6 in Win7 on the original NTFS volume and getting similar error messages (permission denied). I had hoped that ubuntu would avoid the whole permissions issue.

Also, trying to format the same Hitachi HDD 500GB with Master Boot Table option, failed with the following error message:

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
Error: Input/output error during write on /dev/sdb
ped_disk_commit_to_dev() failed

--------------
Win7 & 11.04

---

### Post by Paqman on 2011-05-24
Use the mount point that the drive is mounted to, rather than the actual device. So if /dev/sdb1 is mounted on /media/drive then do:
```
shred -u -n2 /media/drive
```

Shred won't get rid of directories though, just files. It might be easier to just format the drive then use "scrub" to wipe the free space (which, after a format will be the whole drive).

---

### Post by yetiman64 on 2011-05-24
> **merbce said:**
> I tried this  to wipe everything on an external (USB) HDD:
shred -u -n 2 /dev/sdb1

All I got was:  /dev/sdb1: failed to open for writing: Permission denied

Do  I need to set Administrator privileges? I am the only user.
Prior to trying shred, I formatted the volume as Ext4 after trying Eraser6 in Win7 on the original NTFS volume and getting similar error messages (permission denied). I had hoped that ubuntu would avoid the whole permissions issue.

Also, trying to format the same Hitachi HDD 500GB with Master Boot Table option, failed with the following error message:

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdb, scheme=0
got it
got disk
Error: Input/output error during write on /dev/sdb
ped_disk_commit_to_dev() failed

--------------
Win7 & 11.04

Firstly the -u switch will remove the device file in Ubuntu (not a good idea).

You are getting the "permission denied" as a result of not running the command as root with "sudo".

If you want to completely erase the partition /dev/sdb1 (wipe it) you can try the command,
```
sudo shred -f -v -n0 -z /dev/sdb1
```This will entirely reset every bit on the partition sdb1 to 0.

The switches used are,
-f = force
-v = verbose
-n0 = iterations=0 (no overwriting passes as the next switch resets all to bits to 0, also keeps the speed of the operation to a minimum)
-z = zeroing pass.

You will need to reformat the partition after this operation is complete, gparted can do that easily, either from a live-cd or an Ubuntu install.

Please read the man file for shred before use,

```
man shred
```in terminal will allow that.

---

### Post by merbce on 2011-05-25
Thanks yetiman64, that worked perfectly. sudo was just what was needed; it took 8+hours but it worked. I re-formatted with the Disk Utility. The Format Disk failed but Format Volume did a fine job putting NTFS on the disk (for Win7; I'm not ready yet to switch to ubuntu for day-to-day work on a family laptop...).

I then ran chkdsk /f (after chkdsk indicated that there were some problems that limited it to about 14GB of the 465GB available) and got a clean bill of health for the whole disk. Finished up by fomatting with Win7's standard tool. Everything looks good. Now to get some $$$ back from the store (:lolflag:)
Thanks again. This has given me hope that I can resurrect an old Maxtor drive...
All the best.

---

### Post by yetiman64 on 2011-05-25
You're welcome,:)

Please mark your thread as solved if you're problem is fixed, link #5 in my sig has instructions if needed, thanks.

Regards, yetiman64

---

