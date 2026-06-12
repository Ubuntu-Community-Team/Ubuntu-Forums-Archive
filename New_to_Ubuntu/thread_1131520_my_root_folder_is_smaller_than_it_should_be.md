---
title: "my root folder is smaller than it should be"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-20
how do i make it so that i can access my entire hard drive?

my "/" folder is showing as only 22 GB when i want it to be the entire 250GB

---

### Post by cariboo on 2009-04-20
You could use the LiveCD to resize the partition. The reason for using the LiveCD, is you can't work on any of the partitions while they are mounted. Once booted from the LiveCD go to System-->Administration-->Partition Editor. You should be able to resize the partitions there. Be sure you backup any important data first, before doing anything.

Jim

---

### Post by antikristian on 2009-04-20
do a 
```
df -h
```
In a terminal to see how much free space you have on your partitions and their total size.

You might have separate partitions that have more free space, like a /home partition, if / (root) has 22GB available and the rest is used for a /home partition, then that is most likely sufficient for most uses. All your data should be located in /home anyway, / (root) is only for software, logs, temp files and some configuration files for the most part.


How did you come by that number (22GB)
Did you let Ubuntu decide how to partition your drive automatically? 
Did you install it over / besides an old Linux installation or windows installastion?

---

### Post by ayastona on 2009-04-21
when i use the gnome file system browser (i forgot what the hell its called, not dolphin) and i go to my "/" folder it says that it is 22GB total (under properties)...

how do i make it so its 250 GB total (i guess not 250 but 247 GB so that i can still have my swap files)

---

### Post by Volt9000 on 2009-04-21
> **ayastona said:**
> when i use the gnome file system browser (i forgot what the hell its called, not dolphin) and i go to my "/" folder it says that it is 22GB total (under properties)...

how do i make it so its 250 GB total (i guess not 250 but 247 GB so that i can still have my swap files)

Did you read antikristian's post?
S/he basically explained what's happening. When Ubuntu wasn't installed it partitioned your hard drive in such a way that the entire capacity wasn't used. Running that command will show you your current partitions and how much is being used.

You can also run

```

sudo fdisk -l

```

which will also display information about your overall hard drive size.

---

### Post by ayastona on 2009-04-21
**okay first of all:**


> **Volt9000 said:**
> Did you read antikristian's post?
Yes i did.
it took me a bit more searching around to realize what the command he was talking about was really for and that i could type it at any time in terminal/console (watever the hell you wanna call it) 8)

**secondly:**

> **antikristian said:**
> do a 
```
df -h
```
In a terminal to see how much free space you have on your partitions and their total size.

You might have separate partitions that have more free space, like a /home part...

i restarted my computer and now any folder i check in nautilus says that i have 194 GB of free space..:confused:\\:D/:shock: check out the picture attached...

**thirdly:**

so my question... how do i readjust the size of free space allowed for each folder in my drive (and for users?) ... i guess i just need to be educated on how the information is allocated in linux or something...

---

### Post by michy99 on 2009-04-21
The 20 something Gb is the amount of data in your folder. The free space is available to any folder on that partition. As you add files, the folder grows and the free space shrinks. You don't have to do anything.

---

