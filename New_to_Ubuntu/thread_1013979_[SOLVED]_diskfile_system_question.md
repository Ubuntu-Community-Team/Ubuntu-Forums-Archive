---
title: "[SOLVED] disk/file system question"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-17
/dev/sda1: UUID="77f2e095-20b5-44a1-9bdd-a6830cb8c3f0" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="ba12429d-218c-4f45-bb80-90594c29f597"

/dev/sdb1: UUID="ea659ec9-5ee6-4c46-9e02-4eaeb0a76d7c" SEC_TYPE="ext2" TYPE="ext3"

/dev/sdc1: UUID="1bd5aea3-731d-4c4b-95ed-ca7bbcfe3c9a" SEC_TYPE="ext2" TYPE="ext3"

I wonder why only sdb1 and sdc1 show this at the end: " SEC_TYPE="ext2" TYPE="ext3" instead of just TYPE="ext3"

   Where does the " SEC_TYPE="ext2" come from? Could this be a problem?

---

### Post by Pvt_Ryan on 2008-12-17
what command did you run to get that output?

---

### Post by pshootr on 2008-12-17
> **Pvt_Ryan said:**
> what command did you run to get that output?

I believe it was fdisk -1   EDIT: No is wasn't, let me go back and look

---

### Post by rlunger on 2008-12-17
Are sdb1 and sdc1 really ext2 formatted?  ext3 is backward-compatible with ext2.

---

### Post by pshootr on 2008-12-17
> **Pvt_Ryan said:**
> what command did you run to get that output?

Ok, here is what I used to get that.  sudo blkid

---

### Post by pshootr on 2008-12-17
It makes me wonder if I created the partitions as ext2, and then formatted with ext3.   This does not seem rite to me. I seemed to have experianced data loss on one of those drives yesterday. I wonder if this is why?

---

### Post by pshootr on 2008-12-17
> **rlunger said:**
> Are sdb1 and sdc1 really ext2 formatted?  ext3 is backward-compatible with ext2.

Sorry, I overlooked this post. I am not sure really. Thats what I am wondering too. Another thing is I can't look at the free space on these drives. Mabee this is why.

---

### Post by taurus on 2008-12-17
I guess this is the continuation of your other post.  Can you post the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

You already said you can't look at the free space of those drives but why not just post the outputs here so everyone would know why.

---

### Post by pshootr on 2008-12-17
> **taurus said:**
> I guess this is the continuation of your other post.  Can you post the outputs of these commands?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

You already said you can't look at the free space of those drives but why not just post the outputs here so everyone would know why.

I have no excuse. Sorry about that. Here is the output you asked for.


$ sudo fdisk -l

Disk /dev/sda: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46a0469f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         494     3968023+  83  Linux
/dev/sda2             495         524      240975    5  Extended
/dev/sda5             495         524      240943+  82  Linux swap / Solaris

Disk /dev/sdb (Sun disk label): 255 heads, 63 sectors, 4865 cylinders
Units = cylinders of 16065 * 512 bytes

   Device Flag    Start       End    Blocks   Id  System
/dev/sdb1             0      4865  39078112+  83  Linux native

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1 



$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.8G  777M  2.8G  22% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  320K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.7M  249M   2% /dev
tmpfs                 252M     0  252M   0% /dev/shm



$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=77f2e095-20b5-44a1-9bdd-a6830cb8c3f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ba12429d-218c-4f45-bb80-90594c29f597 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by taurus on 2008-12-17
You don't have any entry in /etc/fstab for those two drives and what's wrong with your /dev/sdc?

```

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

Device Boot Start End Blocks Id System
/dev/sdc1 

```
Maybe you want to use gparted and format /dev/sdc1 to ext3 again.

Meanwhile, your /dev/sdb1 looks weird too.  It should start at 1, not 4865 as in your case.  And the "flag" option should be blank instead of 0.  If you don't have anything valuable on that partition/drive, /dev/sdb1, I would use gparted and remove it.  Then, recreate a new partition, /dev/sdb1, starting at the beginning of the drive and ending at the end.

---

### Post by rlunger on 2008-12-17
sda1 shows 'linux' as the file system, while sdb1 shows 'linux naitive'.  I believe that ext3 is classified as 'linux' while ext2 is still 'linux naitive' (because of the widespread adoption of ext2 in linux).  I'm pretty sure that TYPE="ext3" (from earlier) refers to the broad category of the format, while SEC_TYPE="ext2" refers more specifically to the ext2 specification.  ext2 is somewhat a subset of the ext3 format.

---

### Post by pshootr on 2008-12-17
[QUOTE=taurus;6387409]You don't have any entry in /etc/fstab for those two drives and what's wrong with your /dev/sdc?

```

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

Device Boot Start End Blocks Id System
/dev/sdc1 

```
Maybe you want to use gparted and format /dev/sdc1 to ext3 again.

Meanwhile, your /dev/sdb1 looks weird too.  It should start at 1, not 4865 as in your case.  And the "flag" option should be blank instead of 0.  If you don't have anything valuable on that partition/drive, /dev/sdb1, I would use gparted and remove it.  Then, recreate a new partition, /dev/sdb1, starting at the beginning of the drive and ending at the end.[/QUOTE

Well, I only live a few hours away, why don't I just bring it to your house and you can fix it. Just kidding! lol

Yeah it looks like I should re-do each drive. Only problem I can say I know I had is not being able to see free drive space when using df -h

---

### Post by rlunger on 2008-12-17
> **taurus said:**
> You don't have any entry in /etc/fstab for those two drives and what's wrong with your /dev/sdc?

```

Disk /dev/sdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1b0b1b0

Device Boot Start End Blocks Id System
/dev/sdc1 

```
Maybe you want to use gparted and format /dev/sdc1 to ext3 again.

Meanwhile, your /dev/sdb1 looks weird too.  It should start at 1, not 4865 as in your case.  And the "flag" option should be blank instead of 0.  If you don't have anything valuable on that partition/drive, /dev/sdb1, I would use gparted and remove it.  Then, recreate a new partition, /dev/sdb1, starting at the beginning of the drive and ending at the end.

There is no flag value listed for sdb1.  It starts at 0 (no boot record) and ends at 4865.

---

### Post by pshootr on 2008-12-17
> **rlunger said:**
> sda1 shows 'linux' as the file system, while sdb1 shows 'linux naitive'.  I believe that ext3 is classified as 'linux' while ext2 is still 'linux naitive' (because of the widespread adoption of ext2 in linux).  I'm pretty sure that TYPE="ext3" (from earlier) refers to the broad category of the format, while SEC_TYPE="ext2" refers more specifically to the ext2 specification.  ext2 is somewhat a subset of the ext3 format.


Yeah I noticed that before also about sda1 showing 'linux' and the others showing 'linux native' 

Thanks for the insight.

---

### Post by rlunger on 2008-12-17
sdb1 looks fine to me.

---

### Post by pshootr on 2008-12-17
> **rlunger said:**
> There is no flag value listed for sdb1.  It starts at 0 (no boot record) and ends at 4865.

Yeah, I better start from scratch with these drives. Thanks alot for all your help guys.

---

### Post by rlunger on 2008-12-17
Sorry, should have specified what that meant.  There shouldn't be a boot flag for sdb1 because you're not booting from that drive.  The partition starts at 0 (as it should because your not using space on a MBR) and ends at the end of the drive.  Ubuntu is recognizing the drive and partition just fine, so unless you're having a problem with sdb1, I'd leave it the way it is.  sdc1 does look like it needs some work, though.

---

### Post by pshootr on 2008-12-17
> **rlunger said:**
> Sorry, should have specified what that meant.  There shouldn't be a boot flag for sdb1 because you're not booting from that drive.  The partition starts at 0 (as it should because your not using space on a MBR) and ends at the end of the drive.  Ubuntu is recognizing the drive and partition just fine, so unless you're having a problem with sdb1, I'd leave it the way it is.  sdc1 does look like it needs some work, though.

Oh I see. Ok, well thanks alot for the time you took to post this! You :guitar: bro. ):P

---

