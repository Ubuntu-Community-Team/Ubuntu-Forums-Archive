---
title: "Re-installing"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by random turnip on 2009-07-04
My 8.10 is broke, it won't load but i have downloaded and mounted 9.04 to a disk and want to install it over the top of 8.10, i'm also hoping that it will fix the wireless problem.

When installing, am i right in thinking that when i get to the partitioning step, i could just reduce the 8.10 to 0% and that will automatically uninstal it.
I also ahve Vista on here, i intend to give Vista about 65% (for now).

So yeah, i just want make sure that it will uninstal it as there is no use for it if it doesnt boot.

---

### Post by carml on 2009-07-04
If you choose the manual install you can overwrite a partition if you wnat to do,in your case you should do that instead of reducing to 0% the 8.10 partition. :)

---

### Post by poosietgp on 2009-07-07
If your disk has multiple partitions. it is adviseable to use the manual option since it will let you evaluate your partitions and lets you select which partitions you want to format or overwrite.

---

### Post by nhasian on 2009-07-07
hopefully you have a separate /home partition.  if thats the case then you can install the new ubuntu using the manual partitioning option to your root / partition and then tell it to use your existing /home partition.  be careful NOT to tick the format box for your /home partition or it will wipe your data.

if you dont have a /home partition then you should boot off the LiveCD first, backup any critical data you have to an external usb thumbdrive or hard disk, then do a fresh install with separate root and /home partitions.

---

### Post by nothingspecial on 2009-07-07
> **nhasian said:**
> hopefully you have a separate /home partition.  if thats the case then you can install the new ubuntu using the manual partitioning option to your root / partition and then tell it to use your existing /home partition.  be careful NOT to tick the format box for your /home partition or it will wipe your data.

if you dont have a /home partition then you should boot off the LiveCD first, backup any critical data you have to an external usb thumbdrive or hard disk, then do a fresh install with separate root and /home partitions.

You should back up all your critical data which ever way you install. Things can go wrong.

---

