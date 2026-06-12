---
title: "Re-installing an older version of Ubuntu"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by listerdl on 2010-01-09
Hi, I recently installed ubuntu 910 and loved it - but - no sound. There seems to be some massive problem with sound and 910 for me at least and to be honest the hours that it is going to take to fix is simply too time consuming.

I have a dual boot set up.

If I install an earlier version of ubuntu, even like hardy heron which actually works, will that simply overwrite ALL of the buggy 910?

Thanks for all replies!

---

### Post by mjitkop on 2010-01-09
Yes, it will overwrite your existing 9.10.

Did you create a separate /home partition when you installed 9.10? If not, you will lose all your personal files when you reinstall an older version of Ubuntu. Make a backup of your personal files before you start reinstalling Ubuntu. ;)

Even if you have a separate /home partition, it is strongly suggested that you make a backup of your personal files. Personally, I have never lost my personal files in my separate /home partition when installing a different version of Ubuntu over the existing root partition (older or newer version of Ubuntu). In any case, it is always a good idea to have a backup of your personal files anyway. Better be safe than sorry.

---

### Post by kansasnoob on 2010-01-09
You might find this useful:

[http://ubuntuforums.org/showpost.php?p=8633800&postcount=24](http://ubuntuforums.org/showpost.php?p=8633800&postcount=24)

I just linked some screenshots instructing someone else in a reinstallation due to an unrelated problem with Karmic.

**Note: ignore the drive/partition specific instructions like, "be sure to choose /dev/sdc5" and "Be certain to choose /dev/sdc to install grub to".** Those were specific to that machine only :)

---

