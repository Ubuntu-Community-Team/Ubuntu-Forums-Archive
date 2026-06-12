---
title: "Increasing swap file size"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Steveplanetary on 2010-08-05
[SIZE=2]In the 2 weeks that I've been transitioning from Windows XP Pro to Linux I've had to uninstall and reinstall Ubuntu quite a few times.  I'm sure part of it is a hardware problem...my laptop is 8 years old, and I beat on it pretty hard for the last year by streaming video while it was simultaneously crunching numbers for cosmology@home.  That caused Windows to crash a lot, and now my machine just doesn't multitask as well as it used to.

But I know that sometimes Ubuntu has required a hard reboot that led to the uninstall/reinstall thing because the swap file usage was at 100%, and the system was totally unresponsive.  I installed Ubuntu with wubi, and the swap file is the default of 255MB.  I still have 27GB of free space on a 60GB drive, and I want to increase the swap file size to ~1GB, but I don't have a clue about how to do that.

That raises a few more questions:

1) Does Ubuntu have anything like Window's last known good configuration to fall back on?

2) I know Ubuntu has a recovery mode, but what would I do with it?

3) Where would I find a complete list of terminal commands, so I could look up the man pages to learn about the commands?

This thread has covered more ground than I had anticipated, but in helping me (for which I will be very grateful) you will be helping a lot of other newbies too.
[/SIZE]

---

### Post by bcbc on 2010-08-05
> **Steveplanetary said:**
> [SIZE=2]In the 2 weeks that I've been transitioning from Windows XP Pro to Linux I've had to uninstall and reinstall Ubuntu quite a few times.  I'm sure part of it is a hardware problem...my laptop is 8 years old, and I beat on it pretty hard for the last year by streaming video while it was simultaneously crunching numbers for cosmology@home.  That caused Windows to crash a lot, and now my machine just doesn't multitask as well as it used to.

But I know that sometimes Ubuntu has required a hard reboot that led to the uninstall/reinstall thing because the swap file usage was at 100%, and the system was totally unresponsive.  I installed Ubuntu with wubi, and the swap file is the default of 255MB.  I still have 27GB of free space on a 60GB drive, and I want to increase the swap file size to ~1GB, but I don't have a clue about how to do that.

That raises a few more questions:

1) Does Ubuntu have anything like Window's last known good configuration to fall back on?

2) I know Ubuntu has a recovery mode, but what would I do with it?

3) Where would I find a complete list of terminal commands, so I could look up the man pages to learn about the commands?

This thread has covered more ground than I had anticipated, but in helping me (for which I will be very grateful) you will be helping a lot of other newbies too.
[/SIZE]

How to [Increase swap]("https://wiki.ubuntu.com/WubiGuide#How do I increase my swap space?"). There are other interesting things in the guide (like why hard shutdowns break wubi). On that note, you might consider partitioning and doing a direct install if you are using ubuntu so much.

1. No. Since you're using wubi, you could back up your entire root.disk (you can replace the root.disk with a backup and it will be the same (programs and data) as when you backed it up).

2. This is more to get to a recovery menu so you can trouble shoot. You can fix package errors, boot to a console (as root), etc. (but it isn't a magic 'Undo' thing).

3. There're some good beginner's guides out there (can't find it right now). Or search on google for specific things you want to do.

---

### Post by Steveplanetary on 2010-08-05
[SIZE=2]Thanks for the specific info about increasing my swap file space.  It worked as planned.  Thanks also for the reading assignment.  One last question re creating a separate partition for Ubuntu: I know I would have to download and burn a .iso image that is bootable and that contains the tools to create the partition.  On the question of file system, however, and given the number of different file systems supported by Linux, which file system would you consider to be native[/SIZE]  [SIZE=2]to Ubuntu?[/SIZE]  [SIZE=2]Also, I've never partitioned a HDD that already had an OS running on it.  I didn't know it was even possible.

So, question: Where do I find a bootable .iso image to partition the HDD?

Thanks again for your help with the previous question.  I like figuring things out on my own.  That's the best way to learn.  But when you need help, you need help.
[/SIZE]

---

### Post by Elfy on 2010-08-05
You can get the iso here - [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

You will need to check that the iso is good prior to burning it - [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  and alist of the hash sums - [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Then burn it - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then boot with it and install - [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I use ext4 for my partitions, you will be able to access your existing win partitions without changing any of that. 

This might be useful - [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by Steveplanetary on 2010-08-05
[SIZE=2]Thanks for all the links.  I can take care of things from here.[/SIZE]:D

---

