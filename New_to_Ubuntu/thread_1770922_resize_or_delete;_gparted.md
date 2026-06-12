---
title: "resize or delete; gparted"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-05-29
I use HP Mini, and Gparted from USB.

I am not sure whether re-size or delete primary partition to create logical partition prior to ubuntu installation?

---

### Post by wolfen69 on 2011-05-29
It depends. You could just not do anything, install ubuntu and choose "use whole disk" during install set up and it will automatically partition it for you. What are your objectives? Dual boot with windows? Ubuntu alone?

---

### Post by taidaniel on 2011-05-29
Depends on how you want to set it up. I assume you have windows installed on the HP mini. I would suggest you dual boot Windows and Ubuntu and make sure to have 1 or more partition(ntfs)  to share data between Windows and Ubuntu.

I have written a post on this in my [blog]("http://taidanielpc.blogspot.com") but it really depends on how you want to organize your hard disk. You should read and understand more about this before you proceed.

---

### Post by Matrix01 on 2011-05-30
i visited your blog, tai.
and
i clicked your link to disk partition, and
your web page will download advertisement instantly,,,
so unable to read your webpage.

---

### Post by Matrix01 on 2011-05-30
Is existing OS, which is window 7 starter, going to get saved if i choose 'use whole disk'?

---

### Post by wildmanne39 on 2011-05-31
> **Matrix01 said:**
> Is existing OS, which is window 7 starter, going to get saved if i choose 'use whole disk'?
Hi, no it well be over written, if you want to dual boot you can choose install on half the drive, or do you partitioning manually but that is much harder and not as safe for a new person to ubuntu.

---

### Post by Quackers on 2011-05-31
Having a Dell machine I would suggest first that you check the number of primary partitions which are already in use by your Windows system. The maximum is 4. If you try to exceed that number you will have problems!
In Windows open the Disk Management console to check.

---

### Post by taidaniel on 2011-05-31
> **Matrix01 said:**
> i visited your blog, tai.
and
i clicked your link to disk partition, and
your web page will download advertisement instantly,,,
so unable to read your webpage.

Try "[How to Organize and Partition your hard disk]("http://taidanielpc.blogspot.com/2011/05/how-to-organize-and-partition-your-hard_23.html")". I checked my blog and did not get any "popup". 

Anyway, I remember Ubuntu allows you to resize your windows partition during install. If I'm not wrong, I think you can create partitions as well. Just remember to backup before proceeding.

---

