---
title: "Installation options"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by ibates on 2009-06-02
Here is both a question and also some feedback for the writers of the Ubuntu installation software.

When attempting to install Ubuntu 9.04 from the CD, step 4 of the 7 steps in the installation process leads to possibly the most important page in the installation process.  It is where one is asked “do you want to install Ubuntu side-by-side with Windows?” or words to that effect.

At this point two other options are presented - “do you want to install on a separate hard disk?” or words to that effect.   (I will mention the third option later).

Now for someone wanting to install for a dual boot configuration and who has a separate hard disk on which Ubuntu is to be installed, the following problems arise.

When selecting the second option (the separate hard drive option, the first “side-by-side” option becomes unavailable.

Question (not answered in the installation dialogue); if I install to a separate hard disk (option 2), will that set up a dual boot configuration, and, will that leave the Windows partition on the first primary had drive untouched and available, or will that simply install Ubuntu on another hard disk drive and remove access to the Windows partition on the first primary hard drive?

And finally; what is the point of the third “manual partition” option?

Feedback:  By leaving such unexplained options, this installation process falls into a category similar to that which one would expect from Microsoft.  It leaves users who are anxious to protect their original configuration completely bewildered, not knowing if everything is going to be wiped from the original hard drive, or whatever else unexpected may happen.

I cannot find a manual for Ubuntu 9.04 which would explain these option in details.

Any suggestions?

---

### Post by nandemonai on 2009-06-02
You obviously didn't look too hard:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

> When selecting the second option (the separate hard drive option, the first &#8220;side-by-side&#8221; option becomes unavailable.

That's because you're not installing side by side, as in partitions on a single disk, you'll be installing to a separate hard disk.

> Question (not answered in the installation dialogue); if I install to a separate hard disk (option 2), will that set up a dual boot configuration, and, will that leave the Windows partition on the first primary had drive untouched and available, or will that simply install Ubuntu on another hard disk drive and remove access to the Windows partition on the first primary hard drive?

Yes it will not touch the other disk, except to write grub (boot loader) to the MBR IF the other disk is the first disk.

> And finally; what is the point of the third &#8220;manual partition&#8221; option?

To setup a manual partition scheme. Which I'd recommend personally. Gives you much greater control.

> Feedback: By leaving such unexplained options, this installation process falls into a category similar to that which one would expect from Microsoft. It leaves users who are anxious to protect their original configuration completely bewildered, not knowing if everything is going to be wiped from the original hard drive, or whatever else unexpected may happen.

I cannot find a manual for Ubuntu 9.04 which would explain these option in details.

Hardly a fair comparison. Installing an operating system != installing an application. A certain amount of pre-requisite knowledge is assumed and indeed needed. Such as understanding partitioning.

This is what installation guides and docs are for.

As a side note: You should ALWAYS backup your system before installing a new OS, regardless of if you plan to dual boot. It's just common sense. What's to be worried about if you have a recent backup and things go awry?

---

### Post by ibates on 2009-06-02
Many thanks for that info.

FYI; prerequisites are not a problem.  Partitioning procedures etc., are well understood.  What I mentioned was that when one is proceeding in accordance with instructions and those instructions simply stop it is like following street signs which all of a sudden peter out.  You know the feeling I am sure.

This is new territory.  And probably lots of newbies to Ubuntu would prefer not to be "test pilots" having a guess at what is coming next.  Oops ....  (And restoring a backup of a wiped HDD is not a whole lot of fun).

But once again, many thanks.  Your information has been very helpful.

---

### Post by bennachie on 2009-06-02
While you received a comprehensive, clear and polite, response to your question (which is happily not unexpected in this forum - not all forums can claim as much) your fundamental point was worth making - what seems blindingly obvious to a moderately experienced user may not be nearly as obvious to someone exploring a new distribution for the first time.

I agree with you that the options could be presented more clearly at this stage in the installation. On the other hand, most major distributions do try to make sure that you don't stomp all over your existing system unless you really intend to do so, and Ubuntu still sets quite a good example in that respect. However, Mandriva probably does the best job of choosing a sensible default partitioning scheme for the absolute beginner.

Incidentally, I must admit that I normally find it easier to use Google to locate the most appropriate section of the wiki to explore my latest issue or problem, rather than relying on the table of contents.

---

