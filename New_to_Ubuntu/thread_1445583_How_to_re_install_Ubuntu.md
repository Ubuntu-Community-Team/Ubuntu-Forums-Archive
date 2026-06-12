---
title: "How to re install Ubuntu?"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Haseebkhilji on 2010-04-02
i have dual OS windows xp and ubuntu. 
Now i want to remove my previous ubuntu and install a fresh copy.
i have re-install it without formating the (ext4)drive, and it become a kind of overwrite (i think so, because my wallpaper and a few more things are as it was.)
simply want to know how to remove previous one and install a fresh copy on the same drive.

Hope for great reply.

Thanks!

---

### Post by lisati on 2010-04-02
There are a couple of options. Be sure to make a backup of important data first.

One way is to use gParted on your Ubuntu live CD to delete your Ubuntu partition and then reinstall using the largest continuous free space.

Another way is to use manual partitioning, and point the partitioner at your existing partition.

---

### Post by Hreinsi on 2010-04-02
just install it on ext 4 and format if í understand you right

---

### Post by Hreinsi on 2010-04-02
you can move your data to xp and install again if you have space on xp partiton

---

### Post by Hreinsi on 2010-04-02
or you ca
boot into live cd and start the installer. When you get to the partition stage, choose manual, mount all the partitions there to there correct places by clicking on them and selecting properties then select their mount point from the drop down list,

IMPORTANT

When you mount the /home partition make sure the 'format' tick box is UNTICKED. make sure all the others are ticked then do the rest of the install.

all data will be lost but settin players and stuff will be restored after install

---

### Post by yetiman64 on 2010-04-03
<Edit:whole post>

This situation sounds similar to the link below, Im unsure if you want to save a partition (ext4) or do a total cleanout and reinstall. If total reinstall check below.

was/is linked to [http://ubuntuforums.org/showthread.php?t=1443584](http://ubuntuforums.org/showthread.php?t=1443584)

Goto post #9 and #13 if of use
 
view for general info but don't use in whole as won't save ext4 partition . If you consider backing up all ext4 data and starting from scratch it may be of use.

---

### Post by Haseebkhilji on 2010-04-03
is it right, if i do remove my ext4 partition (where my ubuntu is install) and re create it in manual selection.
what about this?

---

### Post by yetiman64 on 2010-04-03
> i have dual OS windows xp and ubuntu. 
Now i want to remove my previous ubuntu and install a fresh copy.If you want to do "a fresh copy" without saving any data or settings etc. the linked thread should work.

If you want to save anything from the previous install it has to be backed up off the HDD as the guide totally removes the old ubuntus partitions.

> is it right, if i do remove my ext4 partition (where my ubuntu is install) and re create it in manual selection.
what about this?     If you are not a more advanced user who knows partitioning, I would certainly advise an automatic install, as is used in the linked thread.

Hope this is of help to you, Take care.

---

