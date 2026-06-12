---
title: "Missing space on Hard Disk"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by grewolf on 2009-06-07
I have a 500 gb sata drive and it states that in the file system properties I have 265.9 gb used.  It is a single partition with 2 users on it.  How do I find out what is using the other 200+ gb

---

### Post by sandyd on 2009-06-07
```

sudo fdisk -l

```
will list all the drives and partitions in your comp

don't trust system monitor

---

### Post by sgosnell on 2009-06-07
Install baobab.  It will show up under Applications/Accessories as Disk Usage Analyzer.  It will show you what is in use by everything, in more ways than you can conceive of.  It will show use by user, by partition, by data type, ad infinitum.

---

### Post by grewolf on 2009-06-08
> **carlee said:**
> ```

sudo fdisk -l

```
will list all the drives and partitions in your comp

don't trust system monitor

> **sgosnell said:**
> Install baobab.  It will show up under Applications/Accessories as Disk Usage Analyzer.  It will show you what is in use by everything, in more ways than you can conceive of.  It will show use by user, by partition, by data type, ad infinitum.

Thank you both.  I used fdisk -l and is it normal for you extend and linux swap to start at the same sector?

I forgot about the disk usage analyzer thank you for the reminder.

---

### Post by oldsoundguy on 2009-06-08
most likely NOTHING is using that UNUSED space, but it is ready to go!

(think about the pie chart in Windows when you go to my computer and click on drive properties.)

---

