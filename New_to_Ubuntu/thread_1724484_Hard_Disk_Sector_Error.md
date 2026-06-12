---
title: "Hard Disk Sector Error"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-08
i wanted to create a swap memory for my ubuntu, so i used Gparted partition manager to resize a logical NTFS partition. and an error occured so it stopped, n now the disk device says it cannot read the last sector or the partition. now the volume size shows it has the previous unchanged size but the device has 2gb less (which went to unallocated space).

i tried returning the unallocated space back to the logical partition but doesnt work.

how can i fix it?

---

### Post by Dutch70 on 2011-04-08
Hi rez182

Check the SMART Data on Disk Utility, it sounds like you may have some bad sectors on your hdd.

---

### Post by rez182 on 2011-04-08
> **Dutch70 said:**
> Hi rez182

Check the SMART Data on Disk Utility, it sounds like you may have some bad sectors on your hdd.
yea i did, there was some bad sectors, but couldent fix it from there. i need a way to match the volume size with device size. (volume size is higher n device size is smaller (the missing space is unallocated)

---

### Post by Dutch70 on 2011-04-08
I don't know how to tell you to match those sizes up and I don't think you'll get those 2GB back.

What I can tell you, is today would be a good day for a back up.

---

### Post by srs5694 on 2011-04-08
I agree with Dutch70. Go to the store to buy a new drive *today*. (Don't mail-order it; the delay could be critically important, since hardware failures can get worse over time -- sometimes very short amounts of time.) Use whatever method you're most comfortable with to transfer everything (or as much as you can read) from the old disk to the new one, then swap drives and throw the old one away.

Good luck!

---

