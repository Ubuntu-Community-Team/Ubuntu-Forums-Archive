---
title: "Cannot Format Old NTFS Partition"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by slappmedoo on 2010-11-01
Hi.

So, I've been browsing through various forums, and I still haven't found a solution this problem (probably because I'm overlooking some obvious detail). I used to dual-boot Vista and Ubuntu, but I haven't booted into Vista in almost a year now. I decided to format that partition to reclaim the 140 GB (140 GB) of unused space.

Using an eHow.com guide (and referring to a couple of forum posts to double check the method), I deleted the ntfs partition with GParted and went to actually format it the space. However, when I right-click the unallocated space in the menu, all of the options except for "New" and "Information" are grayed out. Now I can't figure out what to do to format the space. I don't want to experiment too much, lest I jack up my Ubuntu install.

I've attached a screenshot of GParted as I'm seeing it. Any suggestions?

---

### Post by anewguy on 2010-11-01
You won't be able to format it until you make it a known partition again.  Right now it just thinks it's free space on the disk.  Use "new" to create a partition in that space and mark it to be formatted.  

Dave ;)

---

### Post by slappmedoo on 2010-11-01
That was an inhumanly quick response. Does it matter which file system I create it under? Ubuntu's under ext3, but I don't want to overwrite it.

---

### Post by anewguy on 2010-11-01
I guess it depends on what you want to do with it.  I know that sounds like a dumb response, but it does make a difference.  Do you just want to add this as space to Ubuntu?  If so, I *think* there's a little more involved than that - like do you want the root filesystem there, only user files, etc. - I haven't done it myself, but I have read a few posts on the forum when people wanted to "expand" the amount of space Ubuntu has on the disk, a there are usually a few more steps involved.

Do you want to share any files with Windows (e.g., be booted in Windows and see the files)?

It will make a difference in the partition type and on where it should be mounted.

Dave ;)

---

### Post by slappmedoo on 2010-11-01
I think this is enough info to lurk with. Thanks for the help, Dave!

---

### Post by anewguy on 2010-11-01
Not a problem - please post back if you have any more questions or problems!

Great to see another full-time ubuntu user! I haven't made it that far yet myself, but I'm trying to work out a few things and then I think I will.  I had before, but ran into some problems with video capture, conversion, etc., but I think they may be solved now.

Best of luck!
Dave ;)

---

