---
title: "Accessing data partition from both xp and ubuntu?"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by el_pinguino on 2011-02-27
I have finally decided to try out this "Linux" thing everyone keeps talking about. So I installed Ubuntu on my laptop by shrinking the Windows XP data partition. So what used to be

C: 50 gig XP
D: 250 gig Data 

is now

C: 50 gig XP
D: 200 gig Data
sda1(?): 50 gig lucid lynx

I can still open my files, but is it okay to edit, create, delete files when I move back and forth between the two OS's. Will the file systems get confused? If I edit a document in Linux, will Windows still tell me accurately when the file was "Last Modified" and so on?

---

### Post by travlemon on 2011-02-27
> **el_pinguino said:**
> I have finally decided to try out this "Linux" thing everyone keeps talking about. So I installed Ubuntu on my laptop by shrinking the Windows XP data partition. So what used to be

C: 50 gig XP
D: 250 gig Data 

is now

C: 50 gig XP
D: 200 gig Data
sda1(?): 50 gig lucid lynx

I can still open my files, but is it okay to edit, create, delete files when I move back and forth between the two OS's. Will the file systems get confused? If I edit a document in Linux, will Windows still tell me accurately when the file was "Last Modified" and so on?


Wow, good question!  I don't actually know the answer to that, but I'd like to.  I'm still a Linux "n00b", as I've been using it for only a year.  My educated guess, however, would be that it would accurately show file modification dates and such.

I would think that since Linux has to be compatible with the file system that you're opening the file from, it must write files with full NTFS functionality, including date and timestamps.  I would also guess that the only real "problem" would be if you move the file to a Linux partition, and then move it back to NTFS.  

Try creating a dummy file on your NTFS partition in Windows, then modify it later from Linux and see how it goes.

---

### Post by Yegor on 2011-02-27
Yes,
you still able to work with your data either from Windows or Ubuntu. Just to keep in mind that partition for data should have recognizable file system for both OS (like NTFS). All changes in files will be applied for both system.

---

### Post by oldfred on 2011-02-27
Data partition that NTFS for sharing is a great idea. It reduces the chance that writing into the system partition causes problems. You can read from the windows partition if you want but I would set it to read only. Ubuntu shows all the hidden files in Windows and it is too easy to delete or move an essential windows file.

Do not try to create partitions for Linux in windows, but use gparted.

Shared NTFS partition 
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


or the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
B

---

### Post by ursoouindio on 2011-03-18
Hello.

I already do something like that, have partitions for both Ubuntu and Windows XP systems and other one for mutual data.

Looking at the how-to above I can't tell of anything wrong I've done.

But, using it for a couple of years now, I've found some problems now and then... Sometimes I boot Windows and it starts some file checkings and corrections, before the system loads. One time it got messed up so bad that I lost some files that I've been working on. 

I wouldn't know why that happened, maybe because one Linux app crashed and didn't write correctly the files to the mutual partition. I suspect that it would be caused by Dropbox, since I don't recall having troubles before installing it on both my Ubuntu and Windows systems. Both Dropbox installations access the same folder in the mutual partition.

Now, I am going for a new computer and I would like very much to avoid this kind of problem, as I've lost work before. I wonder if Windows 7 is smarter and wouldn't mess up with the files that Ubuntu changed (maybe improperly). And can you think of something else I could do to guarantee safety for the files that are accessed by both systems?

Thanks!

---

### Post by oldfred on 2011-03-18
Do not know if there are any issues with dropbox.

If you did not have Ubuntu installed and you had the same issues what would you blame? Just as Ubuntu runs fsck every 30-40 boots, you should run chkdsk on windows partitions. The separate shared partition probably never had chkdsk run. Most file type issues are from a file not being closed properly, power failures, system shutdowns, or other issues.

Win7 has some of its own issues. They fixed one grub2 boot issue with flexnet(DRM), but some HP & Dell software still interferes with grub2. Most users just uninstall the HP or Dell software as it has little utility that other software does.

---

### Post by ursoouindio on 2011-03-18
hmm
It just seemed like it was related to Dropbox, can't tell you exactly why because it has been a while ago. I just got concerned about it again because I will get a new pc and want to make it right (not to lose work is an important security thing).

I know Windows XP, I've been using for much longer than Ubuntu and it don't tries to run chkdsk just as a routine test. It does when something is wrong, like corrupted file index for example. Then the files that I was editing on Ubuntu just before were gone (actually, some of then become .chk files, but not all or not entirely). 

As I said, I'm using Windows XP but my next pc will probably come with Windows 7. I believe it has its own (lot of) problems, but I would think that, at this time, Microsoft knows that people sometimes also need other OS and do dual boot, so that originated my question if 7 would be smarter on this. But I don't really expect that.

EDIT: I reread my previous post. One could think I meant Windows 7 is smarter than Ubuntu. I didn't mean that, I was comparing Windows 7 and XP.

---

### Post by JKyleOKC on 2011-03-18
You said, "One time it got messed up so bad that I lost some files that I've been working on." If that was a power failure while you worked on the files in Linux, it's quite possible that not all of the file got written to disk, or that the file's "dirty bit" was set and that forced the run of chkdsk when you rebooted. The same thing can happen with Windows, if you happen to lose power during a critical few milliseconds of its "shutting down" sequence, because it keeps directory information in RAM, in its "buffers" that came in with Win3 and are still part of the design, and writes it back out at shutdown. If a directory sector is only partially written, you can lose many of the files it's supposed to contain.

The best way to prevent such happenings, with any system, is to enable periodic automatic saves. Microsoft Word offers the feature, as do a number of *nix packages. With this enabled, only a few minutes worth of your work (that done since the last autosave) is ever at risk, and loss of entire files is almost impossible unless the whole disk goes bad...

---

### Post by ursoouindio on 2011-03-18
> **JKyleOKC said:**
> You said, "One time it got messed up so bad that I lost some files that I've been working on." If that was a power failure while you worked on the files in Linux, it's quite possible that not all of the file got written to disk, or that the file's "dirty bit" was set and that forced the run of chkdsk when you rebooted. The same thing can happen with Windows, if you happen to lose power during a critical few milliseconds of its "shutting down" sequence, because it keeps directory information in RAM, in its "buffers" that came in with Win3 and are still part of the design, and writes it back out at shutdown. If a directory sector is only partially written, you can lose many of the files it's supposed to contain.

The best way to prevent such happenings, with any system, is to enable periodic automatic saves. Microsoft Word offers the feature, as do a number of *nix packages. With this enabled, only a few minutes worth of your work (that done since the last autosave) is ever at risk, and loss of entire files is almost impossible unless the whole disk goes bad...

I remember some of the files were just renamed and moved as .chk by windows, while other chk files were composed by pieces of the other work files and thrash.

I remember the problem went with latex files and some images. It wasnt a power failure, but could be one of those ram buffer things. Maybe I shut down Ubuntu while Dropbox was downloading those files?
Any way to prevent that?

I don't know if it really is related to Dropbox, it just seems like. It got updated to a newer version since that episode. Maybe it is safer now.

---

### Post by oldfred on 2011-03-18
Are you hibernating in Windows. That will cause data loss, if any file in the hibernation is changed or moved as it expects no changes. If booting two (or more) system and sharing data, you should not hibernate.

---

### Post by ursoouindio on 2011-03-18
> **oldfred said:**
> Are you hibernating in Windows. That will cause data loss, if any file in the hibernation is changed or moved as it expects no changes. If booting two (or more) system and sharing data, you should not hibernate.

I did hibernated for some times, but soon realized it was trouble. But then, the trouble I got was with external storage drives. Since I detected that as a dangerous thing, I stopped doing it.

This problems I related this are different. Windows messed up the files while booting, not waking up.

But thanks for the advice :)

---

