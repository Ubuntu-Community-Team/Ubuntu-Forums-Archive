---
title: "How do I convert an ext4 to ext3?"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-06-20
Xubuntu was too heavy for an old computer so I have Puppy Linux on it, and everytime I try to install it, it seems to install, but it actually doesn't. It turns out the ext4 from Xubuntu isn't supported. I'm in gparted right now, and I can't seem to do anything (all options are greyed out). I can create a partition table, but it's saying it'll delete everything which is fine because there's nothing on it, but will I be able to convert it to an ext3 then?

---

### Post by VastOne on 2010-06-20
> **Legendary_Bibo said:**
> Xubuntu was too heavy for an old computer so I have Puppy Linux on it, and everytime I try to install it, it seems to install, but it actually doesn't. It turns out the ext4 from Xubuntu isn't supported. I'm in gparted right now, and I can't seem to do anything (all options are greyed out). I can create a partition table, but it's saying it'll delete everything which is fine because there's nothing on it, but will I be able to convert it to an ext3 then?

Are you in gparted from a livecd?  It does not make sense that you cannot delete the drive and set it up the way you want unless the partition is in use.

---

### Post by -kg- on 2010-06-20
From where are you running GParted?  Hopefully, you're running it from Live CD.  If you're running it from the Xubuntu installation itself, that would mean that partition is mounted (it has to be in order to run), and you can't perform partitioning operations on a mounted partition.  Also, you must click on and select the partition you want to do the operations on.  If you haven't selected a partition, the options will be grayed out.

If you are running from a Live CD (either the Xubuntu or GParted Live CD) and all (or most) of the options are still grayed out, check to see if the partition is mounted.  There should be an option in the right click menu that says "Unmount".  If there is, unmount the partition.  You should then be able to select other partitioning operations, including what you are looking for.

> I can create a partition table, but it's saying it'll delete everything which is fine because there's nothing on it, but will I be able to convert it to an ext3 then? 

I wouldn't mess with the "Create A Partition Table" portion.  Regular operations are much easier.  There's a reason you can't select other procedures.  

If there's nothing on the partition, you should just choose the "Format To:" option and choose ext3.  This will reformat the partition to ext3 no matter what the present file system type is.  It will also wipe out any information in that partition, but since you said there's nothing on it anyway, it doesn't make any difference.  If there is information on it, however, make sure you back up anything you need.

A good guide to partitioning operations (especially using GParted) can be found at the link in my signature block.

I'm kind of amazed that Puppy won't recognize ext4, though.  Do you have the latest...version 5?  It's called Lucid Puppy, because it is based on Ubuntu Lucid.  I would think that it would also recognize ext4 as a result, but of course, I could be mistaken.  I use Puppy, but not much.  My nephew could probably tell you, but he's not here.

---

