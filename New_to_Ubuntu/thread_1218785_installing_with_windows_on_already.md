---
title: "installing with windows on already"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Dayofswords on 2009-07-21
i have a 20gb hard drive with all partition on windows xp, about 6 gb used up. How can i push all the data to one side for windows and on a separate created partition at 10 GB then install ubuntu? will a simple defrag do it?

---

### Post by w4ett on 2009-07-21
do a defrag on your NTFS partition and then use the guided partitioner on the live cd to create your required partition for Ubuntu.

---

### Post by earthpigg on 2009-07-21
> **dayofswords said:**
>  will a simple defrag do it?

yup. ideally, several defrags. how much patience do you have?

---

### Post by lisati on 2009-07-21
> **dayofswords said:**
> will a simple defrag do it?

Sometimes "several" defrags will be useful. You might also want to take the time to clean out temporary files from your system.

---

### Post by prshah on 2009-07-21
> **dayofswords said:**
> i have a 20gb hard drive with all partition on windows xp, about 6 gb used up. How can i push all the data to one side for windows and on a separate created partition at 10 GB then install ubuntu? will a simple defrag do it?

Yes, a simple defrag is enough. With only 6 GB used, it is unlikely you need additional defrags. Also, parted (CUI) from version 1.5.5 onwards is smart enough to push any leftover data further in.

---

### Post by 3rdalbum on 2009-07-21
When you reach the bit in the installer where you specify that you want to resize the Windows partition: Make sure you drag the little handle in the bottom bar chart to give Ubuntu the amount of space that you want.

Recently it seems a few people haven't noticed the little sliding handle, and have partitioned only 2.5 gigabytes (the minimum, and the default) for Ubuntu. As soon as they try and install updates, they run out of space.

---

### Post by JHan816 on 2009-07-21
Thanks for the information. I am going to be doing this soon and it helps...
 
--John

---

### Post by SunnyRabbiera on 2009-07-21
To be honest dual booting on such a small hard drive is a big waste of time.
With windows hogging up at least 10GB alone with updates windows on such a small drive will seriously undermine a dualboot.
My suggestion: Hold out and maybe dual boot on a newer computer, or if possible upgrade your hard drive space.
But upgrading hard drive space can be tricky, depending on the type of computer you have.
If this is a old netbook or something dont bother with a dual boot, its just not enough space.

---

