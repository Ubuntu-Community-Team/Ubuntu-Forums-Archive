---
title: "/home"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by oxygenfarm on 2011-04-29
I see the wisdom of maintaining a separate "/home" partition, and am not afraid to try, but would appreciate detailed instructions.
How do I create partition "/home" and tell Ubuntu about it?
Thanks.

---

### Post by Calash on 2011-04-29
If this is a current install that you want to migrate you can follow the following directions

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

For a new install from disk you will have to go to the advanced partitioning and set the partitions there.  I am having trouble finding a tutorial for that but once I do I will post it.

---

### Post by beew on 2011-04-29
> **oxygenfarm said:**
> I see the wisdom of maintaining a separate "/home" partition, and am not afraid to try, but would appreciate detailed instructions.
How do I create partition "/home" and tell Ubuntu about it?
Thanks.

During install choose maunal partition and then you can choose your layout. Create an ext4 partition and label it as / (about 15 -20g would be more than enough) Create another ext4 partition as large as needed and label /home,  then create a swap partition 1.5xram and then proceed.

Next time when you install a new version  of Ubuntu (or reinstall ) , follow the same procedure and choose the same /home partition** but make sure you don't format** it then your settings and data will be saved.

---

### Post by oxygenfarm on 2011-04-29
> **beew said:**
> .....Next time when you install a new version  of Ubuntu (or reinstall ) , follow the same procedure and choose the same /home partition** but make sure you don't format** it then your settings and data will be saved.

 I read that to mean a reinstall of Ubuntu would then go to "/" but "/home" would be untreated?

---

### Post by rosencrantz on 2011-04-29
Exactly - but you'd better make sure that during a new install your /home partition isn't formatted like the root partition /

---

