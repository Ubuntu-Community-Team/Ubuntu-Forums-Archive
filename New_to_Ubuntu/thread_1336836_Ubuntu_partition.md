---
title: "Ubuntu partition"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by BALJEET OBEROI on 2009-11-24
[font=arial black]hi everybody there " good morning "[/font]
i am new to ubuntu
 i am going to install ubuntu on completely formated windows pc 
[font=arial black]i need seperate partition for data storage[/font] os that if it gets corrupted 
i donot lose data 
[font=arial black]how shall i procede during partition stage while installation[/font] 
shall i use manual or automatic partition 
 
[font=arial black]thanks in advance [/font]

---

### Post by overdrank on 2009-11-24
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by 3rdalbum on 2009-11-24
Linux partitions don't seem to get corrupted anywhere nearly as frequently as other operating systems. Probably because it checks the filesystem every 30 boots.

If you want a seperate partition for your home directories, then you will need to use the "manual" partitioning. Create the partitions the way you want them; the system/applications partition needs to be given the mount point of "/". The documents partition needs to be given the mount point "/home". When you go to create the partition there will be a popup menu asking what mount point you want, so that part is easy.

The filesystem type should be "Ext4" in both cases.

As far as sizing goes, my / is on a 160 GiB HDD, but is only using 6 GiB. So don't go overboard with the amount of space that you give to /. I'd say 20GiB should be big enough for almost anyone.

---

