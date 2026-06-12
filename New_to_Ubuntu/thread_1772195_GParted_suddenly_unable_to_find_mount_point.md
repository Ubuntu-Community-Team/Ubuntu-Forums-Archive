---
title: "GParted suddenly unable to find mount point"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-05-31
Last week, GParted (inside Ubuntu) managed to see all my disks & partitions (main drive & 2 USB HDD's with multiple partitions) OK.
I just rechecked the screenshots - no problem.

This morning, I launched GParted but then changed my mind almost immediately & closed the GP window, assuming that would stop the actions OK.
But I noticed that the main disk activity light stayed on for quite some time & I was unable to unmount one HDD - "busy".
In the end, I shut down the PC (normally) & hoped that would safely handle the HDD.

After unplugging the HDD, rebooting & replugging the HDD, all seemed OK - Nautilus could see & read the HDD OK.

But when I fire up GParted again, it has a warning sign on one ext3 partition of this one HDD, with message:
```
Warning
Unable to find mount point
Unable to read the contents of this file system!
Because of this some operations may be unavailable.

The following list of software packages is required for ext file system support: e2fsprogs.
```

I checked SynApt & e2fsprogs is shown as installed.

Note the second HDD has a similar mixture of ext3/FAT32 partitions (I use them for alternate backups) & GParted sees them all OK.

I rebooted etc but still no success.

I read several threads with similar titles but did not understand what to check next.

Thanks for any help!

---

### Post by FormatSeize on 2011-05-31
Have you tried to mount it manually? This happens to me sometimes (normally the DVD drive), and I have to mount it manually through the terminal. 
 
What do you see when you input the following command in a terminal:
```
hdparm
```

---

### Post by 2CV67 on 2011-05-31
OK - I fixed it by changing the name of the partition from "Iomega Linux" to Iomega_Linux" & rebooting.

Confirmed by changing back to Iomega Linux (Warning!) & back to Iomega_Linux (OK).

Don't understand why it worked OK with Iomega Linux last week & I have the screenshot to prove it!

---

