---
title: "partition help"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-04-28
Somehow when i installed 9.04, my partitions got jacked up. I ended up with 200GB of unmounted space. I have attempted to fix this with gparted. But, I have a 34Gb space on one side and a 180GB space on the other. I cannot get them to join into the space that I am using. What am I doing wrong? I just want the whole disk to be the same partition... 

Please help me.

---

### Post by pancham on 2009-04-28
Even I have the same problem,  I dont even know where my 200 gb hard disk space has gone,, its showing only 19gb home directory.....

---

### Post by kansasnoob on 2009-04-28
How about a screenshot of what you have? I'm a gui guy!

Like here's mine:

[ATTACH]111497[/ATTACH]

Edit: You may have to install gparted to take the screenshot! Just go to terminal and run:

sudo apt-get install gparted

---

### Post by pancham on 2009-04-28
Now how to use the unallocated space

---

### Post by wizard10000 on 2009-04-28
> **pancham said:**
> Now how to use the unallocated space

The dialog box says you can't have more than four primary partitions and that's correct.  extended partitions go *inside* a primary partition so sda5 actually sits inside sda4.  If you extend sda4 into the rest of the unused space you can create partitions in there.

---

### Post by pancham on 2009-04-28
how do you extend sda4 to use unpartitioned space,,,, when I selected sda4 and clicked Device/Create partition table,,,, it said this would delete all the data on the disk,,, so how to include the unused space without affecting the data...

---

### Post by wizard10000 on 2009-04-28
> **pancham said:**
> how do you extend sda4 to use unpartitioned space,,,, when I selected sda4 and clicked Device/Create partition table,,,, it said this would delete all the data on the disk,,, so how to include the unused space without affecting the data...

First, never alter a partition table without having a good backup  :)

Now that that's out of the way...

You run gparted and down in the partition list you right-click sda4 and select "Resize/Move" - but the partition can't be mounted, so you'll have to do it with a live CD.

---

### Post by chilimac02 on 2009-04-28
Here's my screenshot.

the second partition (the small one) is the one that is currently being used.

-Justin

[IMG]http://farm4.static.flickr.com/3353/3483373152_e874a08be2.jpg?v=0[/IMG]

---

