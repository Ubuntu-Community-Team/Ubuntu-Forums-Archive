---
title: "Swap:  since file allowed, why not automatically create/manage it?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by anewguy on 2009-12-04
In another thread by another user I posted back a couple of questions and learned that you can have a swap file instead of a swap partition.  Basically, as I understand it, unless a swap partition is on another drive on another controller, there is no advantage to a swap partition versus a swap file (unless you are running more than 1 version of Linux, but that's a different matter).  I posted a question at the end of that thread that was never answered, so I thought I'd post it here looking for an answer.

Since swap can be a file instead of a partition, why not:

(1) automatically create a swap file at installation and manage it's size automatically (like "another" OS does), thus eliminating the hassle of creating a swap partition?

(2) after the above, could not a more "advanced" user create a swap partition and use it versus the swap file if desired?

Just curious, as I *think* that most of the "regular" desktop users who might try Linux/Ubuntu probably have "stock" PC's - that is, a single hard drive on a single controller.  Why confuse a newbie more at installation time by recommending (if not "forcing") to create a swap partition?

Just curious........

Dave :)

---

### Post by jbrown96 on 2009-12-04
There are certainly advantages to having a swap partition. A file system is very organized: the data is stored in a pattern, there are journals (to avoid losing info if the system crashes during a write), and there's meta data (permissions, modification times, etc.). Everything that is written to a file system has to conform to the way that that the file system wants it. This leads to a certain amount of overhead. 

Swap doesn't need permissions, doesn't need metadata, and isn't persistent (we don't need to recover it, if the system crashes). Therefore, putting it in a file system is slower for no gain. 

How much slower depends on the file system, but I doubt it would be by much. However, it can be very slow if the file system has to allocate space when writes are necessary. Splitting the swap file into smaller pieces (fragmentation) leads to really bad read/write times, so you want to make the swap file one large, contiguous piece on the disk. Do you see where I'm going with this? Basically the swap file needs to be a fixed size (so it can be allocated as a contiguous piece). If it's fixed sized, and can't be moved in reasonable fashion, then why not move it outside the partition (it will always be [slightly] faster)?

Performance-wise there are no arguments for putting swap inside a file system. However, as you say #1, it would be much easier for users if it was automatically created during installation. Then again, there is the guided partitioning mode for users that can't setup partitions. 

Windows does have a variable sized swap file, but if you look closely it's not that variable. Most of it is statically allocated, and if you need more space then that, there is a tremendous performance penalty to allocate new space (especially if the drive is fragmented because it might have to allocate many small chunks rather than one large one). 

My take on swap is that it's unnecessary. I've used linux for several years on several systems (ranging from 1GB to 6GB ram). I used to create big swap partitions (2-2.5x ram), but they were literally never used. I stopped creating swap about a 1.5 years ago. I have never had any trouble. I use virtualization to host an XP installation on my 2GB laptop; I allocate 900MB to XP, and I still don't have any problems with running out of ram. Swap just doesn't seem to be useful. I haven't tried systems with <1GB, so maybe it's useful there (but computers with <1GB are quickly becoming a small minority). 
I think Ubuntu should stop recommending swap. The system should reserve  a small chunk of space on the file system (maybe 200MB) for emergency swap. It could then allocate more as needed. The idea is that situations where even the 200MB (statically allocated) would be needed would be exceedingly rare that the possibility of a large penalty for allocating new swap space is so remote that users would never have a problem with it. 

I completely agree that when a user is setting up a system they have no idea what swap is. Some of them ask questions here about, and I hear about 8 out of 10 people chiming in with the 2x ram recommendation. That information is so old, but no one takes any time to think about it. You literally just throw that disk space away.

Linux does not need much ram. Let's face it, almost all computers are designed with windows in mind, which needs much more ram. Therefore, almost all computers could almost be said to have "too much" (I know, you can't have too much of a good thing) ram. Linux doesn't have anything really cool like Vista's/7's SuperPreFetch, so there's nothing to take advantage of all that ram. Applications in Linux also pervasively use shared libraries, so individual applications don't take much memory either.

---

### Post by cascade9 on 2009-12-04
> **jbrown96 said:**
> Windows does have a variable sized swap file, but if you look closely it's not that variable. Most of it is statically allocated, and if you need more space then that, there is a tremendous performance penalty to allocate new space (especially if the drive is fragmented because it might have to allocate many small chunks rather than one large one). 

My take on swap is that it's unnecessary. I've used linux for several years on several systems (ranging from 1GB to 6GB ram). I used to create big swap partitions (2-2.5x ram), but they were literally never used. I stopped creating swap about a 1.5 years ago. I have never had any trouble. I use virtualization to host an XP installation on my 2GB laptop; I allocate 900MB to XP, and I still don't have any problems with running out of ram. Swap just doesn't seem to be useful. I haven't tried systems with <1GB, so maybe it's useful there (but computers with <1GB are quickly becoming a small minority). 
I think Ubuntu should stop recommending swap. The system should reserve  a small chunk of space on the file system (maybe 200MB) for emergency swap. It could then allocate more as needed. The idea is that situations where even the 200MB (statically allocated) would be needed would be exceedingly rare that the possibility of a large penalty for allocating new swap space is so remote that users would never have a problem with it. 

As far as windows goes..you really dont want a swap file smaller than your ram. Swap files on windows arent just for when you run out of ram, it also dumps the ram contents to swap for windows to examine later in the case of (some) errors. 

Also, its a good idea to actually go into windows and change the dynamic allocation of swap file size. You can also do what I've been doing for years....make a 'pseudo-swap partition'. Win still uses a swap file, but if you make a partition a bit bigger than your swap file size, and move swap there, you'll get less fragmentation.

---

### Post by anewguy on 2009-12-04
Thanks for the excellent reply!  I didn't think there could be any way for a file, with it's inherent overhead, to be the same as having a separate partition.  Answers given to posts in the other thread had indicated there was no difference, no performance hits, and that just didn't seem viable to me.

I don't know how the internals of swap work in Linux, but I know on the big boxes I used to work on the I/O was much different than to a normal file - things like the channel programs setting up the I/O to swap at the maximum track size for the device, etc..  This did make things quicker than a file system.

I know in Linux you supposedly don't get fragmentation and hence no need for a defrag, but surely (again, I don't know the internals of how the file system works in Linux) it just seems logical that data would get fragmented - the file system isn't going to reorg files to keep everything contiguous, so at some point data is going to be all over the disk (that's my take on it).

I would say this though - even though the swap may not be getting touched by a lot of "normal" users, it would be needed for laptop users (or at least some form of memory image file) for suspension (if that even works for very many users - seems to be a lot of posting regarding that not working the best, but I suspect that is video, wireless, etc., drivers not getting restarted).

So, thanks again for a great reply!

Dave :)

---

### Post by 3rdalbum on 2009-12-04
The process of creating a swap partition is automatic. It's so automatic that when I installed 9.10 I forgot to tell it not to create a swap partition. It's certainly no hassle to the user to create one, and the performance of a partition is better than that of a file.

Downside: I lost 6 gigs of hard disk space.
Upsides: 

If a program goes mad and tries to use all my memory (has happened) it gets swapped out; the low responsiveness and high hard disk noise warns me that something is going wrong, and I have time to switch to a VT and kill whatever process it is before the machine crashes. Without swap, it would probably crash without much warning.

I can now hibernate; something I never tried before, since I never had swap before. (I still prefer to suspend, but during a storm I would hibernate).

---

### Post by jbrown96 on 2009-12-04
> **anewguy said:**
> I know in Linux you supposedly don't get fragmentation and hence no need for a defrag, but surely (again, I don't know the internals of how the file system works in Linux) it just seems logical that data would get fragmented - the file system isn't going to reorg files to keep everything contiguous, so at some point data is going to be all over the disk (that's my take on it).
Dave :)

This isn't true. All file systems have fragmentation issues. Windows has such a bad reputation from when it used Fat32 for system drives. Fat32 fragments very badly. NTFS, especially newer versions (newer than in XP), are actually very good at preventing fragmentation. 
Linux FS get fragmented as well. Generally, it's not as much of a problem for at least the following two reasons. #1 linux uses less disk space. This means you usually have large partitions that have lots of free space, which really helps reduce fragmentation. #2 Linux does not usually move files around. Most things the OS dynamically creates (info about hardware, kernel, etc.) are not actually stored to disk; they reside in memory. Look at ```
mount -l
``` and note all the "none" (and "proc") entries. More of this stuff tends to get written to disk in Windows, and since it's constantly changing, there is a greater likelihood of fragmentation because of the constant disk allocations/deallocations. I have also heard that Linux file systems are better. I tend to agree with this, but it is probably not that significant (compared to new versions of NTFS). 

The real reason why you don't hear about fragmentation on Linux is because there aren't tools to fix it. Linux users tend to be evangelists (including me at times!), and so they say fragmentation doesn't exist because there are no tools to fix it. XFS does have support for defragging, but you can't do it on a mounted file system. Ext4 is in the processing of getting a defrag tool (that supposedly can be used on mounted systems). People tend to hide their faults; why would Linux users promote the discussion of things they can't fix?

What I tend to find with Linux is that there aren't many people that really understand it well. Mist hear/read something that was published years ago in some blog or article, and then they repeat it forever. That's being harsh; everyone does this to some extent. What was true 10 years ago -- that Linux has significantly less fragmentation than Windows -- is not true now. 

The problem is how would people learn this. Obviously, really technical people would know the truth, but that's because they read technical mailing-lists and do the coding. The rest of people get their info form forums and article/blogs. If I really like doing X (using linux), why would I want to read articles about how X is inferior to Y (Windows, the "arch nemesis" of Linux :roll:). These articles don't get written, or are dismissed as trolling. Linux user (and probably other groups too; I just follow linux and its communities closely) don't take (constructive) criticism well. We get defensive, and take pot shots at parts of Windows (or whatever) that were poorly designed. The problem is that they don't bother to update their facts over time. You get people bemoaning the same stuff about Windows constantly: registry, fragmentation, dll hell, etc. The problem is that most criticisms are horribly out of date. 

> I would say this though - even though the swap may not be getting touched by a lot of "normal" users, it would be needed for laptop users (or at least some form of memory image file) for suspension (if that even works for very many users - seems to be a lot of posting regarding that not working the best, but I suspect that is video, wireless, etc., drivers not getting restarted).
This is true for hibernation not suspension. Hibernate needs free swap space equal to the current amount of ram+swap in use. This can be problematic, especially with swap in use. The usual recommendation is to create swaps that are twice as larg as ram, presumbably so if all your ram + part of swap is in use, then you can still hibernate. I tend to think this is foolish, because you waste even more disk space for a feature that isn't used very often and is pretty stupid (my opinion). I don't like hibernate becauase it's really slow. You have to copy all the data in ram to swap, and then run the hibernate shutdown process. This is almost always slower than a shutdown/startup cycle. I know in KDE you can have all open programs start from your last session, so it's not even an issue of hibernate convenienantly opening your apps. However, I do really like suspend; that's a really great feature that I use all the time on my laptop, but it doesn't require swap.
For hibernation, I still think users would be better off with a swap file in a partition. The only situation where I can see significant swap use is during hibernate, so the swap file can grow large for hibernate, and basically disappear (except for some "emergency swap", maybe 200MB) when the system is running. Then you are not always losing 2-2.5x ram all the time, and should only lose ~<ram during hibernate.

---

### Post by anewguy on 2009-12-04
Hibernation is what I actually meant - couldn't think of the term last night so I put in suspension, forgetting that people use that term as well.

Dave :)

---

