---
title: "Weird fstab/mounting drives on startup issue"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by schlitz100 on 2010-04-25
I have 3 drives that mount on startup. I edited the fstab one of the first things after installing to add these drives and it always worked for months. I haven't installed anything new or changed anything in a week or so but yesterday I boot up and none them mounted. I edited the fstab and comment blocked the 3 lines and was able to mount them manually after rebooting. Then I removed the #'s and rebooted and this time one drive mounted. Then I #'d the 2 drives the didn't mount rebooted, removed the #'s and rebooted then 2 of the drives mounted. So now I have 2 of the drives mounting on bootup and the 3rd won't. Except for adding and removing #'s I haven't changed the fstab. I am absolutely clueless as to why this is happening all of a sudden or how to get this last drive to mount on boot up again. Any insight would be appreciated.

I'm using 9.1 64bit

---

### Post by Morbius1 on 2010-04-25
Post the output of the following commands and let's see if fstab is pointing to the right partitions - don't know why it would have changed by itself but you never know:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**

---

### Post by schlitz100 on 2010-04-25
jason@jason-sinistar:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="aa53d2cc-5389-4312-be5e-d118f68179b2" TYPE="ext3" 
/dev/sda5: LABEL="DVDs" UUID="93e2e5b0-93b5-4dd6-b346-774083da44d9" TYPE="ext4" 
/dev/sda6: LABEL="New" UUID="d413e01a-f56f-4dfb-bc7c-363924787ff3" TYPE="ext4" 
/dev/sda7: UUID="01C983E9C553EC80" LABEL="Other" TYPE="ntfs" 
/dev/sdb1: LABEL="Files" UUID="a9ac4b90-c00a-4c86-9825-eca23c0c7983" TYPE="ext4" 
/dev/sdb5: UUID="fd990e39-dd1d-49dd-8857-c09b172f4740" TYPE="swap" 
jason@jason-sinistar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=aa53d2cc-5389-4312-be5e-d118f68179b2 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fd990e39-dd1d-49dd-8857-c09b172f4740 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6 /media/New ext4 defaults 0 0
/dev/sdb1 /media/Files ext4 defaults 0 0
# /dev/sda5 /media/DVDs ext4 defaults 0 0
jason@jason-sinistar:~$ 

-----------------------------------

DVDs is the one not mounting on boot (when the # is removed)

---

### Post by Morbius1 on 2010-04-25
Unfortunately I don't see anything wrong with that line in fstab.

The only thing that is odd is the last "0". The last digit controls the relative order of a filesystem check on boot. Your system partition is set to "1" but the last 3 are set to "0" which means never.

*I usually set all but the linux system partition ( which I set to "1" ) to "2", with the exception of the Windows OS system partition which I set to "0" and make read only.*

It's possible the partition got corrupted.

You can do a manual check:

**1st**: Make sure that /dev/sda5 is unmounted.

**2nd**: run fsck:

sudo fsck -f /dev/sda5

Other than that I really have no idea why it wont mount.

---

### Post by themusicalduck on 2010-04-25
You could try using UUID to identify a partition instead of /dev/sda, etc.

To find out the UUID of a disk, you can run ```
sudo blkid
``` in a terminal. Then use ```
UUID="uuid"
``` in fstab in replacement of /dev/sda6 or whatever.

So for e.g. I have this in my fstab - 

```
UUID=492C872062EFDB85       /media/Stuff   ntfs-3g    defaults,umask=0 0 0

```

To mount an ntfs drive. Ext UUIDs look more like this though: 776d758c-e242-4335-905d-3b0ec8db5673

---

### Post by schlitz100 on 2010-04-25
> **Morbius1 said:**
> Unfortunately I don't see anything wrong with that line in fstab.

Ran fsck, changed the 2nd 0 to 2's on the 3 drives. booted it up, none mounted. played with and now I can only get one to mount on boot. Very strange.

---

### Post by Morbius1 on 2010-04-26
Every time this happens, which sounds like every time you reboot run the following command again:

[B]sudo blkid -c /dev/null

[/B]Does it match the original:> /dev/sda1: UUID="aa53d2cc-5389-4312-be5e-d118f68179b2" TYPE="ext3" 
/dev/sda5: LABEL="DVDs" UUID="93e2e5b0-93b5-4dd6-b346-774083da44d9" TYPE="ext4" 
/dev/sda6: LABEL="New" UUID="d413e01a-f56f-4dfb-bc7c-363924787ff3" TYPE="ext4" 
/dev/sda7: UUID="01C983E9C553EC80" LABEL="Other" TYPE="ntfs" 
/dev/sdb1: LABEL="Files" UUID="a9ac4b90-c00a-4c86-9825-eca23c0c7983" TYPE="ext4" 
/dev/sdb5: UUID="fd990e39-dd1d-49dd-8857-c09b172f4740" TYPE="swap" 

---

### Post by schlitz100 on 2010-04-27
ok after ignoring it for a while then trying to mount on boot all 3 seem to work now... for now.

---

