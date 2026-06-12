---
title: "How do I reformat an external hard drive?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Bearly Able on 2010-11-07
Hi,

I did a fresh install of 10.10 yesterday, following a major problem with my system which had been running 10.04.  I set up sbackup as before, to backup to an external hard drive, but every time it runs, it throws an error message along the lines of "Error writing to file: file too large."

I've searched the forums and found [this thread]("http://ubuntuforums.org/showthread.php?t=1606323&highlight=sbackup"), indicating that the problem is with the FAT32 file system on my external drive.

Can I simply use gParted or Disc Utility to reformat the drive to ext3 or ext4?  Which is recommended?

Thanks for your help.

Lesley

---

### Post by HotShotDJ on 2010-11-07
Right-click on the external drive's desktop icon.  You'll see an option to format in the pop-up menu.

---

### Post by jroa on 2010-11-07
> **Lesley Lutomski said:**
> Hi,

I did a fresh install of 10.10 yesterday, following a major problem with my system which had been running 10.04.  I set up sbackup as before, to backup to an external hard drive, but every time it runs, it throws an error message along the lines of "Error writing to file: file too large."

I've searched the forums and found [this thread]("http://ubuntuforums.org/showthread.php?t=1606323&highlight=sbackup"), indicating that the problem is with the FAT32 file system on my external drive.

Can I simply use gParted or Disc Utility to reformat the drive to ext3 or ext4?  Which is recommended?

Thanks for your help.

Lesley

I don't know why you would have formatted as FAT32, but you might want to check to see if it is first.  GParted should tell you what the format is.

If it is formatted as a FAT format, then you should be able to reformat and reinstall with little work.  I use ext3, but I do not have enough experience with either to recommend one over the other.  I only use it because it is older and my thinking is that therefore it will be more compatible.

---

### Post by Azrael3000 on 2010-11-07
I would recommend disc utility. It is more user-friendly imho.

---

### Post by HotShotDJ on 2010-11-07
> **jroa said:**
> I don't know why you would have formatted as FAT32, but you might want to check to see if it is first.  GParted should tell you what the format is.

If it is formatted as a FAT format, then you should be able to reformat and reinstall with little work.  I use ext3, but I do not have enough experience with either to recommend one over the other.  I only use it because it is older and my thinking is that therefore it will be more compatible.
jroa:  I believe the OP has an external drive formatted as FAT32, not the drive that he has Ubuntu installed upon.

---

### Post by HotShotDJ on 2010-11-07
> **Azrael3000 said:**
> I would recommend disc utility. It is more user-friendly imho.More user friendly then right-clicking on the drive's desktop icon?  I can't imagine!  :)

---

### Post by Bearly Able on 2010-11-07
Thanks for the quick replies.

> **jroa said:**
> I don't know why you would have formatted as FAT32, but you might want to check to see if it is first.  GParted should tell you what the format is.

I didn't format it - that's the way it came, and it's not particularly old.  It is definitely FAT32 - I'd already checked after reading the other thread.  (It had never occurred to me to do so before.)

There are some files on the drive from the manufacturer, which will obviously be deleted if I reformat.  As far as I can tell, there's nothing significant there, but what do I know?  Until half an hour ago, I didn't know I had a problem!

---

### Post by jroa on 2010-11-07
> **HotShotDJ said:**
> jroa:  I believe the OP has an external drive formatted as FAT32, not the drive that he has Ubuntu installed upon.

Yes, I believe that you are right.  But the back up is FAT32 and that is what I was questioning.  I would not purposely format a drive as any FAT format unless I had to, such as needing to use it with a win9x system.

---

### Post by tjandracom on 2010-11-07
> Originally posted by **Lesley Lutomski**
Can I simply use gParted or Disc Utility to reformat the drive to ext3 or ext4? Which is recommended? 

Yes, you can. gParted is so simple, i think. But why don't you try it both and find yourself which one is suitable for you. Everyone has its own preferences... It's a new drive, isn't it? So you have nothing to lose...

---

### Post by jroa on 2010-11-07
> **Lesley Lutomski said:**
> Thanks for the quick replies.



I didn't format it - that's the way it came, and it's not particularly old.  It is definitely FAT32 - I'd already checked after reading the other thread.  (It had never occurred to me to do so before.)

There are some files on the drive from the manufacturer, which will obviously be deleted if I reformat.  As far as I can tell, there's nothing significant there, but what do I know?  Until half an hour ago, I didn't know I had a problem!

Ok, that makes sense.  I can not help directly with your problem, but in future, I would recommend you first reformat as ext3 or ext4 if you intend to use the drive with Linux and NTFS if with Windows.

---

### Post by Bearly Able on 2010-11-07
> **jroa said:**
> ... in future, I would recommend you first reformat as ext3 or ext4 if you intend to use the drive with Linux and NTFS if with Windows.

I certainly will.  I'd have done so this time if I'd known about the problem.

I went with HotShotDJ's suggestion of right-clicking, which gave me three formatting options - ext2, ext4 or FAT32(!).  I've reformatted as ext4 and sbackup has backed up without complaint.

Thanks to everyone who replied.

---

