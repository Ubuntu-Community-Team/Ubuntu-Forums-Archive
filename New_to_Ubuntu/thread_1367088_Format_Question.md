---
title: "Format Question"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-12-29
Hey guys,

I have a 750GB external hard drive. And I made a 50GB partition on it, and formatted it to WBFS, so I can add Wii games to it, and play the games off the hard drive.

Well, I've recently gotten a 500GB external that I'm going to use just for the Wii. So I want to format the 50GB WBFS partition on the 750GB external.

So, what is the best way to go about this with Gparted? Here's a pic of my external through Gparted:

[IMG]http://lookpic.com/i/893/ZqTTX096.png[/IMG]


That unknown 50GB partition must be my WBFS partition, right? So, since the rest of the external is formatted to FAT32, 

Do I: 

just format that 50GB partition to FAT32? That way that partition will become with the rest of the FAT32 external? 

Or do I:

Just delete that 50GB partition? That way that partition will become with the rest of the FAT32 external?

Hope you can understand what I'm asking, I'm not the best at explaining things.

Thanks for any help.

---

### Post by glubbdrubb on 2009-12-29
I take it that what you want to do is merge the "unknown" 50Gb partition with fat32 partition?

Are you running your system off the fat32 partition?

---

### Post by h8uthemost on 2009-12-29
Yes, I want to merge it.

As for your second question, I'm not sure what you mean. I'm using the external to store all my music, movies, tv, etc. I'm not running an OS off of it.

I should have formatted it to FAT or ext3 when I first got it, but I'm stuck with FAT32 right now. Thanks for the reply.

---

### Post by Paddy Landau on 2009-12-29
Delete the 'unknown' 50Gb partition (sdb2).

If you want, you can then resize the FAT32 partition (sdb1) to expand it into the unused area.

Warning: There is a (small) chance of failure when doing the second step, so please back up your data first.

(If you back up your data first, that will allow you to reformat the entire drive as ext3, ext4 or NTFS.)

---

### Post by glubbdrubb on 2009-12-29
Back up the data on your drive.

First, delete the unknown 50 Gb partition.

Then unmount the external drive by going into a nautilus window (the file explore) and click the "eject" button next to the drive in question.

Then (back in Gparted) click on the big fat32 partition and click "Resize/Move".

I don't know what it will ask for next but you should be able to figure it out.

---

### Post by h8uthemost on 2009-12-29
Ok, thank you for the help guys. I don't really have anywhere to back these files up to, so I'm hoping this is going to ok and I don't lose anything.

---

### Post by glubbdrubb on 2009-12-29
If it works out then just mark this thread as solved please, using the "Thread Tools" at the top of the page.

I hope it works out

---

### Post by Paddy Landau on 2009-12-29
> **h8uthemost said:**
> I don't really have anywhere to back these files up to, so I'm hoping this is going to ok and I don't lose anything.
You realise, of course, that your hard drive could fail at any time? If you don't have backups, you're guaranteed to lose data eventually.

---

### Post by h8uthemost on 2009-12-29
^ Yep, I do know that. And I will be picking me up a couple TB externals for backup purposes pretty soon. But at this moment I have no where to backup all this data to change the format of the external.

Anyways, I did what you guys suggested and everything went well. I deleted the unknown partition, then just resize the main one. And I know have 50GB more space on the main partition.

Thanks a lot for your help guys. It's appreciated.

---

