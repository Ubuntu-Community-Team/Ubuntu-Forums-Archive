---
title: "Problems mounting NTFS partitions"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by andy_blah on 2009-04-29
I had 2 partitions previously used by Window$(not installed on them), tried to restart it to boot into Ubuntu (so I could remove it to re-arrange the partitions and re-install Window$). I tried to mount the two NTFS partitions in Ubuntu, but this is what it says: 

```
/dev/sda2 looks like swapspace - not mounted
mount: you must specify the filesystem type
```

And this image shows that sda2 is actually the NTFS partition, and what error GParted displays when I click the information entry from the partition's menu:
[IMG]http://i61.photobucket.com/albums/h41/andy_blah/screenshot_001.png[/IMG]

I suppose that when I restarted from Windows the last time, it didn't "unmount" properly the partitions, this happened to me before, but what should I do now to fix this issue?

---

### Post by sahabcse on 2009-04-29
Hi Try the following command

mount -t ntfs-3g /dev/sda2 /media/windisk -o force

The directory windisk must exist in /media folder. For more info click [here]("http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html")

---

### Post by andy_blah on 2009-04-29
```
ntfs_mst_post_read_fixup: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

This is the output of that command. Unfortunately I can't boot into Windows (because I removed it) or to install it

---

### Post by sahabcse on 2009-04-29
If you haven't removed the windows means try to repair the winodws

---

### Post by andy_blah on 2009-04-29
I **have** removed Window$, and **can't** install it ^_^;

---

### Post by sahabcse on 2009-04-29
similar issue this may help

[http://ubuntuforums.org/showthread.php?t=650954](http://ubuntuforums.org/showthread.php?t=650954)

---

### Post by andy_blah on 2009-04-29
I can't mount it in LiveCD either, and GParted displays the same error in LiveCD :(

---

### Post by sahabcse on 2009-04-29
Anyway, if it says "unable to read the contents of this file system", try from windows, to run defragmentation and ScanDisk for NTFS partition - . with windows tools, or a specific program which I think works better than windows built-in tools, If you haven't windows means try to use winodws LIVE CD.

---

### Post by zeex on 2009-04-29
> **andy_blah said:**
> ```
ntfs_mst_post_read_fixup: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

This is the output of that command. Unfortunately I can't boot into Windows (because I removed it) or to install it

Hi, 

try this 

```
$ sudo apt-get install ntfsprogs
``` 

ntfsprogs is a very good package, contains a collection of tools to work on NTFS filesystem. see manual.

To fix /check your NTFS drive ( say for example /dev/sda6 is your NTFS drive)

```
$ sudo ntfsfix /dev/sda6
```

---

### Post by andy_blah on 2009-04-29
> **sahabcse said:**
> Anyway, if it says "unable to read the contents of this file system", try from windows, to run defragmentation and ScanDisk for NTFS partition - . with windows tools, or a specific program which I think works better than windows built-in tools, If you haven't windows means try to use winodws LIVE CD.

Try to understand, I can't boot into Window$, since I have removed it, meaning that I don't have installed it anymore, and can't install it since I don't have any available partitions to be able to install it to. I am using Window$ XP, not Vi$ta, so I can't use Window$ LiveCD unfortunately

> **zeex said:**
> Hi, 

try this 

```
$ sudo apt-get install ntfsprogs
``` 

ntfsprogs is a very good package, contains a collection of tools to work on NTFS filesystem. see manual.

To fix /check your NTFS drive ( say for example /dev/sda6 is your NTFS drive)

```
$ sudo ntfsfix /dev/sda6
```

Thank you for this, but unfortunately it doesn't work either, it displays those error messages:

```
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
```

Is there any utility like chkdsk that can be booted from a floppy or pen drive?

---

### Post by zeex on 2009-04-29
> **andy_blah said:**
> 
Is there any utility like chkdsk that can be booted from a floppy or pen drive?

Hi, 

There is a boot CD [Hiren's Boot CD]("http://en.wikipedia.org/wiki/Hiren%27s_Boot_CD")  primarily for MS-DOS. You'll find chkdkk utility there. 

I've to warn you though there is some leagal issue with this CD 

> Due to the inclusion of illegally copied copyrighted works, Hiren's Boot CD is legally considered "warez" and pirated intellectual property; downloading and/or possessing the CD has various legal implications according to the person's global location, such as violation of the Digital Millennium Copyright Act in the USA.

So if there is no legal issue related to downloading/possessing  this CD in your location then go ahead :) . This should solve your problem. Try this and see what happens  and use /f option with chkdsk ( $ chkdsk e: /f  , assuming drive letter is e)

Although ntfsfix should have worked. Unmount the drive before runing ntfsfix and run as root.

---

### Post by andy_blah on 2009-04-29
Thank you for your suggestion, but I don't have any blank CDs at the moment, would be interested in something that can be booted off a pen drive or floppy disk. I also used Partition Magic in attempt to check the partition, and it tells me this: "Error number 1507 - Severity: Critical - Bad file record signature"

When I used ntfsfix I did run it as root and couldn't have mounted the volume anyway (that's why I want to solve this problem ^_^

---

