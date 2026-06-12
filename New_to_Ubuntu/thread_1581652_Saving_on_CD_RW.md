---
title: "Saving on CD RW"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by bodach on 2010-09-25
I hope this is a dumb question!

I moved to Ubuntu a few months ago and am gradually porting all my application from Windows. Currently I'm using 10.04 having worked up from 9.04. I don't think I had the following problem in 9.10, but am not certain.

A couple of days ago I wanted to make an archive copy of some files to a CD RW, with a view to updating it at a later date. I discovered that I couldn't use "Save as" to make a copy directly from Open Office. Further experimentation showed that I can't copy any files or folders onto a CD RW or DVD RW disc. The error message is always that the media are Read Only. However, CDROMS are mounted as 1 & 0, respectively, and I can start a project in Brasero or K3b which will write to an RW disc, but no addition to the disk is possible.

I feel I must be making a really simple error - can anyone help?

Thanks.

---

### Post by MartyBuntu on 2010-09-25
> **bodach said:**
> ...but no addition to the disk is possible.



Make sure you have **Multisession** enabled in K3B.
It leaves the disk "open" for further writing.

---

### Post by bodach on 2010-09-25
> **MartyBuntu said:**
> Make sure you have **Multisession** enabled in K3B.
It leaves the disk "open" for further writing.

Thanks, that could help in some situations, but the real problem is that I can't save files directly to a CD or DVD. I can save to other removable media such as a flash drive.

I can't figure out why I always get a "Read Only" error when I try to do a direct save to the optical drives. I also get a read only error if I try to format the drive. Similarly I can't directly unmount the drive, although k3b seems to be able to.

---

### Post by Mark Phelps on 2010-09-25
You can't write files directly to a CD, be it CD-R or CD-RW.

You have to "burn" the files using a CD-writing program.  It formats a session and then transfers that session to the media.  If you have multi-session enabled for the media, the writing program can add another session to the media.

But, a CD is not a filesystem like a hard drive, meaning, you can't just drag-and-drop files or folders to it.

---

### Post by ieee488 on 2010-09-25
> **bodach said:**
> I hope this is a dumb question!

I moved to Ubuntu a few months ago and am gradually porting all my application from Windows. Currently I'm using 10.04 having worked up from 9.04. I don't think I had the following problem in 9.10, but am not certain.

A couple of days ago I wanted to make an archive copy of some files to a CD RW, with a view to updating it at a later date. I discovered that I couldn't use "Save as" to make a copy directly from Open Office. Further experimentation showed that I can't copy any files or folders onto a CD RW or DVD RW disc. The error message is always that the media are Read Only. However, CDROMS are mounted as 1 & 0, respectively, and I can start a project in Brasero or K3b which will write to an RW disc, but no addition to the disk is possible.

I feel I must be making a really simple error - can anyone help?

Thanks.

What you want to do is called packet writing.
Read [http://ubuntuforums.org/showthread.php?t=129093](http://ubuntuforums.org/showthread.php?t=129093)
It explains the fundamentals

---

### Post by bodach on 2010-09-25
> **ieee488 said:**
> What you want to do is called packet writing.
Read [http://ubuntuforums.org/showthread.php?t=129093](http://ubuntuforums.org/showthread.php?t=129093)
It explains the fundamentals

Thanks!

I knew I was being stupid, but coming from Windows I expected to be able to do the same things as I did there such as saving files to CD. I did not realise that Windows had packet writing installed by default, but the "How To" also explains why I had problems with some of my homemade MS Data Discs!

Thanks to all for your help and interest!

---

