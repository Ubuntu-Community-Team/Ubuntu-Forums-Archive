---
title: "Please Help"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by imgoddogmi on 2008-12-09
Ok So I got the Cd working, but one problem. When I am in the installation stage, phase 4, the partitioner does not allow me to pick my partition.  What I did was partition my h.d before Ubuntu and so I have winxp on one partition and wanted the other partition for ubuntu.  But when I am trying to install ubuntu, the partition part does not have an option for my other partition. It has several choices but it seems to me like it's gonna repartition my h.d.  

What you guys think?  Thanks in advance for your help.

---

### Post by slammed87d21 on 2008-12-09
I had the same issue. Partition your hdd so XP takes the whole drive, and then when you try to install, you should be able to partition properly.

---

### Post by bumanie on 2008-12-09
If you choose the manual partitioning option you will be able to direct the ubuntu installation to go where you want it to.

---

### Post by Peter09 on 2008-12-09
I've always found the best way is to delete all partitions / space that i **want** Ubuntu to use. Gparted will do this for you. 

The partitioner seems to prefer to use areas that are not formatted rather than partitions that already exist, it presumes you want to keep them.

---

### Post by jimmy the saint on 2008-12-09
From the live CD, delete the partition you want to install it on(system>administration>partition editor).  THEN start the installation process.  Be careful and back up your data first.  During the installation, just choose to use the unused space and let Ubuntu take care of the partitioning for Ubuntu.

---

### Post by hyper_ch on 2008-12-09
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by igknighted on 2008-12-09
Note also that Ubuntu (or any *nix install) will need at least 2 partitions.  One can be rather small, and is used as swap space (basically a ram overflow).  The other is where the root file system (called /) will be.  This is (in closest windows terms) the c:/ drive.

As others have said, select manual partitioning and delete the partition in that space.  Then create a swap partition (if your ram is <1gb, use 2xram; if ram is >1gb, use the ram size).  In the partition creation dialog it should let you format it as swap.  Then fill the rest of the space as an ext3 partition, and set it to be mounted as /.  These should all be options in the create partition dialog.  Then move on and let it apply the changes and you should be good to go.

---

