---
title: "Installed ubuntu to save files from damaged hd, need to move ubuntu to other drive."
date: 2009-01-31
forum: New to Ubuntu
---

### Post by IzNohGod on 2009-01-31
Hi!

I was having trouble with Xp:roll: (the hd made some noise when starting windows)
I bought a 500gb hd to save files. Since the other disk was full.

I installed ubuntu 8.04 on the 500gb. and copied the files from the other hds. I had to manually mount the drives because windows didn't close properly. 
This took all day:(

But dont want the OS on my new 500hd, I have two other hds, one 40gb and one 200gb.

The 200gb is the one that failed, but still working.

So how to I move ubuntu without moving the backup files to the other drive? 
Or could I just format the other drives, remove ubuntu(without delete backups), and install it on another drive?  (Possible?)
And how do I rescue the 200gb hd? 

Thanks in advance.

---

### Post by taurus on 2009-01-31
You don't have to install Ubuntu if you want to move files from one harddrive to another harddrive.  You can do that with Ubuntu LiveCD.  All you have to do is to mount those drives from the LiveCD and start moving your files over.

---

### Post by IzNohGod on 2009-01-31
yes, but i did. now i want to remove ubuntu or move it to another drive,
but still have the files..anyway to do that?

---

### Post by taurus on 2009-01-31
Unless you saved your files on a separate partition (of the same harddrive), removing Ubuntu means deleting Ubuntu's partitions (/ & swap).  Therefore, all the files on / will be destroyed too.

---

### Post by handydan918 on 2009-01-31
> **IzNohGod said:**
> yes, but i did. now i want to remove ubuntu or move it to another drive,
but still have the files..anyway to do that?

Check out rsync
```
man rsync
```

Something like ```
rsync -av <source_directory> target_directory>
```

---

### Post by IzNohGod on 2009-01-31
Lol, so I have to start all over again..Format the 500gb, Use LiveCD and move files to the disk, and format the other drives with LiveCD and then install ubuntu on preferred drive?

Or is it possible to partition the drive, then remove ubuntu safely?

---

### Post by ugm6hr on 2009-01-31
I'm unclear on what you have done on the 500GB HD.

It sounds like you used the entire HD to install Ubuntu on (presumably using the "Guided - Use entire disk" option).

If so - your 500GB HD is formatted as ext3 (unless you manually selected something else).  There is no way to "remove" Ubuntu from its own partition, although I suppose you could boot a LiveCD and delete all the folders except where the files you want to keep are.  That would just leave a useless GRUB on the MBR, which will do no real harm since you won't be booting from that HD in any case.  However, "Ubuntu" (as in the fully installed OS) takes about 5GB of space, which is almost nothing on a 500GB HD.

Are you planning on using Ubuntu at all?

If not - you would be better off with an NTFS partition on the HD to back everything up on to.  ext3 does work with XP, but if you are genuinely not using Ubuntu, what would be the point?  While starting from scratch may seem a bit of a nuisance - you may as well get things sorted for your future use now.

---

### Post by IzNohGod on 2009-01-31
> **ugm6hr said:**
> I'm unclear on what you have done on the 500GB HD.

It sounds like you used the entire HD to install Ubuntu on (presumably using the "Guided - Use entire disk" option).

If so - your 500GB HD is formatted as ext3 (unless you manually selected something else).  There is no way to "remove" Ubuntu from its own partition, although I suppose you could boot a LiveCD and delete all the folders except where the files you want to keep are.  That would just leave a useless GRUB on the MBR, which will do no real harm since you won't be booting from that HD in any case.  However, "Ubuntu" (as in the fully installed OS) takes about 5GB of space, which is almost nothing on a 500GB HD.

Are you planning on using Ubuntu at all?

If not - you would be better off with an NTFS partition on the HD to back everything up on to.  ext3 does work with XP, but if you are genuinely not using Ubuntu, what would be the point?  While starting from scratch may seem a bit of a nuisance - you may as well get things sorted for your future use now.

yes, your correct, I made that mistake. Im now formating the 500gb drive with gparted, but im unsure if I should remove all the partitions. I've got the partition 
/dev/hdd1
and a unallocated partition about 2.8gb. that i cant delete.
should i format the /dev/hdd1? would that remove the unllocated space?

Im going to use ubuntu but not on that hd:)

---

### Post by taurus on 2009-01-31
Post a picture of gparted with your /dev/hdd.

---

### Post by ugm6hr on 2009-01-31
So is your data now safely backed up somewhere else? It would be a real nightmare if the previously dying HD actually completely died while you erase the new 500GB HD.

You never said if you wanted to keep Ubuntu or not.

If not - just install Windows wherever you want, then reformat the HD from Windows and copy files across from backup (either using Windows or LiveCD).

---

### Post by IzNohGod on 2009-01-31
> **ugm6hr said:**
> So is your data now safely backed up somewhere else? It would be a real nightmare if the previously dying HD actually completely died while you erase the new 500GB HD.

You never said if you wanted to keep Ubuntu or not.

If not - just install Windows wherever you want, then reformat the HD from Windows and copy files across from backup (either using Windows or LiveCD).

No backup at the moment. hers the pic:
[IMG]http://img443.imageshack.us/img443/3513/48878308fb2.png[/IMG]
By [iznohgod](http://profile.imageshack.us/user/iznohgod) at 2009-01-31

---

### Post by ugm6hr on 2009-01-31
You have presumably already formatted it in NTFS.  Ubuntu is not installed there.

---

### Post by IzNohGod on 2009-01-31
hmm, but how to remove the unallocated space? or should I just ignore it?

---

### Post by taurus on 2009-01-31
Delete /dev/hdc1 (I think that is what it said from the screenshot) with gparted.  That would make the whole drive unallocated.  Now, create a new partition, /dev/hdc1, taking up the whole harddrive.  Format it to whatever filesystem you want, probably ntfs since you that was what you had before.

---

### Post by IzNohGod on 2009-01-31
Thanks alot. Really appreciate it. 

Final Question>
How do Iclose the thread?

---

