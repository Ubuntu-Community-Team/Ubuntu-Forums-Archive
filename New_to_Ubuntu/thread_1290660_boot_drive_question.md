---
title: "boot drive question"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by ah pook on 2009-10-13
Hm. I was trying to be proactive, as I have a very old 30G drive where my /
resides. So without out thinking, I copied the entire disk, hidden files and everything, over to a spare 80G drive that was empty. Now, the 80G has disappeared, the 30G is still hidden, and I was just wondering where the 80G went..if I go to Places/computer/filesystem, everything is still there, but did I somehow make one disk out of the two?

Not really a problem if it is, I'm just curious..

thanks in advance...

---

### Post by cariboo on 2009-10-13
Could you paste the output of:

```
sudo fdisk -l
```

in your next post.

---

### Post by ah pook on 2009-10-13
sure - 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091d82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

---

### Post by ah pook on 2009-10-23
anyone? I'd really like to get rid of the 30 gig, as it's slowly failing, and boot from the 80 gig, but I'm not sure how to do it..

---

### Post by GimmeCoffe on 2009-10-23
Mount the drive from the terminal.

~GimmeCoffe

---

### Post by egalvan on 2009-10-23
> **ah pook said:**
> sure - 
```
[COLOR="Red"]Disk /dev/sda: 80.0 GB[/COLOR], 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

[COLOR="Red"]Disk /dev/sdb: 160.0 GB[/COLOR], 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

[COLOR="Red"]Disk /dev/sdc: 30.7 GB[/COLOR], 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris

[COLOR="Red"]Disk /dev/sdd: 500.1 GB[/COLOR], 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux
```

you show four hard drives
sda  <-- has one primary partition
sdb  <-- has one primary partition
sdc  <-- has one primary partition, and one extended partition
sdd  <-- has one primary partition

is this correct?

---

### Post by ranch hand on 2009-10-23
This is jaunty?

---

### Post by ah pook on 2009-10-24
yes, it's jaunty...

---

