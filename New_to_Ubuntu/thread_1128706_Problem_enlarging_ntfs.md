---
title: "Problem enlarging ntfs"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Veehmot on 2009-04-17
As you can see, sizes differs.
In Windows XP, I have 4.9GB, but I allocated 10GB with GParted.

[IMG]http://img10.imageshack.us/img10/2561/screenshotvwx.png[/IMG]

Why is this?

---

### Post by unutbu on 2009-04-17
Please open a terminal (Applications>Accessories>Terminal), type
```

sudo fdisk -l
df -T
```
and post the output.

---

### Post by Veehmot on 2009-04-17
**[SIZE="4"]sudo fdisk -l[/SIZE]**

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa376a376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        2734    11478442+   5  Extended
/dev/sda5            1306        2610    10482381   83  Linux
/dev/sda6            2611        2734      995998+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26752674

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
```

**[SIZE="4"]df -T[/SIZE]**

```
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda5     ext3    10317828   2269200   7524512  24% /
tmpfs        tmpfs     2027728         0   2027728   0% /lib/init/rw
varrun       tmpfs     2027728       100   2027628   1% /var/run
varlock      tmpfs     2027728         0   2027728   0% /var/lock
udev         tmpfs     2027728      2804   2024924   1% /dev
tmpfs        tmpfs     2027728       104   2027624   1% /dev/shm
lrm          tmpfs     2027728      2380   2025348   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0  iso9660      715810    715810         0 100% /media/cdrom0
```

---

### Post by unutbu on 2009-04-17
/dev/sda1 did not show up in the output of "df -T". Perhaps it was not mounted.

In a terminal, how about type
```

sudo mount /dev/sda1 /mnt
df -T
```
and post the output once more.

---

### Post by Veehmot on 2009-04-17
**[SIZE="4"]df -T[/SIZE]**

```
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda5     ext3    10317828   2323056   7470656  24% /
tmpfs        tmpfs     2027728         0   2027728   0% /lib/init/rw
varrun       tmpfs     2027728       104   2027624   1% /var/run
varlock      tmpfs     2027728         0   2027728   0% /var/lock
udev         tmpfs     2027728      2804   2024924   1% /dev
tmpfs        tmpfs     2027728       104   2027624   1% /dev/shm
lrm          tmpfs     2027728      2380   2025348   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0  iso9660      715810    715810         0 100% /media/cdrom0
/dev/sda1  fuseblk     5116668   4978920    137748  98% /mnt
```

---

### Post by unutbu on 2009-04-17
To enlarge the NTFS partition:
```

sudo apt-get install ntfsprogs
sudo umount /dev/sda1
sudo ntfsresize /dev/sda1
sudo mount /dev/sda1 /mnt
df -T
```

The output of df should show sda1 to have about 10GB of total space.
It should show up in Windows XP that way too.

It appears GParted changed the size of the partition, but did not adjust the size of the filesystem inside the partition. The above commands should fix that.

---

### Post by Veehmot on 2009-04-17
Well I have a problem. ntfsprogs is obsolete, as it says in the output:

**[size=4]sudo apt-get install ntfsprogs[/size]**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ntfsprogs has no installation candidate
```

---

### Post by unutbu on 2009-04-17
Which version of Ubuntu are you using?

(ntfsprogs is not obsolete -- its is alive and kicking in Intrepid -- but you may not have the right repository activated.)

---

### Post by Veehmot on 2009-04-17
Well I have Ubuntu Intrepid 8.10 64-bit version. How can I check the current repository activated?

---

### Post by Veehmot on 2009-04-17
Nevermind, I just updated Synaptic packages and it went right:

[size=4]**sudo apt-get install ntfsprogs**[/size]

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 285 not upgraded.
Need to get 383kB of archives.
After this operation, 942kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ar.archive.ubuntu.com intrepid/main libntfs10 2.0.0-1ubuntu2 [114kB]
Get:2 http://ar.archive.ubuntu.com intrepid/main ntfsprogs 2.0.0-1ubuntu2 [268kB]
Fetched 383kB in 5s (66.7kB/s)    
Selecting previously deselected package libntfs10.
(Reading database ... 99174 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_amd64.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

[size=4]**sudo ntfsresize /dev/sda1**[/size]

```
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 5239468544 bytes (5240 MB)
Current device size: 10733958144 bytes (10734 MB)
New volume size    : 10733953536 bytes (10734 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 5099 MB (97.3%)
Collecting resizing constraints ...
WARNING: Every sanity check passed and only the dangerous operations left.
Make sure that important data has been backed up! Power outage or computer
crash may result major data loss!
Are you sure you want to proceed (y/[n])? y
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sda1'.
```

[size=4]**df -T**[/size]

```
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda5     ext3    10317828   2525072   7268640  26% /
tmpfs        tmpfs     2027728         0   2027728   0% /lib/init/rw
varrun       tmpfs     2027728       108   2027620   1% /var/run
varlock      tmpfs     2027728         0   2027728   0% /var/lock
udev         tmpfs     2027728      2804   2024924   1% /dev
tmpfs        tmpfs     2027728       104   2027624   1% /dev/shm
lrm          tmpfs     2027728      2380   2025348   1% /lib/modules/2.6.27-7-generic/volatile
/dev/scd0  iso9660      715810    715810         0 100% /media/cdrom0
/dev/sda1  fuseblk    10482376   4979080   5503296  48% /mnt
```

---

### Post by unutbu on 2009-04-17
ntfsprogs is in the "main" repository. Try clicking System>Admin>Software Sources. Under "Ubuntu Software" tab, make sure there is a checkmark next to "Canonical-supported Open Source software (main)".

Then close the window. It should update your software sources if necessary.

If it was already enabled, then try this:

In a terminal, type
```

sudo apt-get update
```
If there is an error, post the output.
If there is no error, try
```

sudo apt-get install ntfsprogs
```
again.

---

### Post by Veehmot on 2009-04-17
Im in Windows XP now, and it all went great, thanks for your time.

So is this the right method to follow in a need to resize a ntfs partition?

---

### Post by unutbu on 2009-04-17
GParted lists ntfsprogs as a "Suggested" package, but not a strict dependency.
Therefore, GParted will semi-operate without the ntfsprogs package, but if you resize an NTFS partition without first installing the ntfsprogs package, then you end up having the problem you encountered.

Now that you have the ntfsprogs package installed, you should not have any more problem resizing NTFS partitions using GParted.

---

