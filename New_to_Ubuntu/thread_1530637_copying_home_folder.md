---
title: "copying home folder"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by crew51m on 2010-07-13
I would like to do a clean install of 10.4, I would like to back up my home folder, it is 26 gig, will Ubuntu continuously keep copying onto the dvd's asking for new media when media is full, will it compress it to fit onto a dvd or will I have to copy each file to the dvd's?

---

### Post by k3lt01 on 2010-07-13
I can't actually answer your question but just a thought, wouldn't it be cheaper and more usable in the long run just to buy a USB external hard drive?

Also if you have a separate /home partition you wont need to do this unless you think there is something wrong in it.

---

### Post by Fastjack77 on 2010-07-13
Hi crew51m,

You might want to compress the folder and split the compress files into writable chunks:

[http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/](http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/)

Than burn each compressed files. Also, compressing the home folder into one big file and using "split" and "cat" later could be easier.

---

### Post by ghostborg on 2010-07-14
If you want a clean install I would backup your personal files, music, etc to an external hard drive.
My system is setup with two internal hard drives. Just my preference.
 I have one internal drive for the root partition (/) and swap and another internal drive just containing my /home folder. You will need to use the custom partition option during the install. This will allow you to reinstall Ubuntu if needed. Just remember to use the custom partition option during a re-install and do not format the home partition.
Remember to backup your browser bookmarks, a common oops.
Backup, backup, etc.
I am not a big fan of compressed backups because if something goes wrong you loose it.
If you use DVD's I would just copy the files you want to keep to a data DVD as is.
I have in the past used my gigabit network to temporarily copy files to another computer with lots of space. Snore.

---

### Post by crew51m on 2010-07-14
Thanks, I like the ext drive idea, I have a couple laying around I will play around with it.

---

