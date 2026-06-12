---
title: "path to network drives and backup issue"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by eeeek on 2009-09-28
I have a question that I should already know after a couple of years of using Ubuntu (and other Linux versions). But anyways...

How do I browse to the path of a networked drive? Is that possible? What directory are mounted network drives under? 

The only way I really understand how to access a network drive is opening up Nautilus and clicking on "Network" Is there another way of opening it up.

For example - I am in need of backing up about 80 GB of data in /home. (I'm probably getting into what should be a new thread, here). I installed Grsync, but I don't see how to browse to a network drive.

Here's the deal. My main hard drive won't boot. I installed Ubuntu (8.04 64 bit) on another old HDD and have them both hooked up in the same box. I can see and read everything on my main HDD just fine - it's all there, it just can't boot off that drive.(my guess is it's a GRUB issue).

I have another basement computer (Win XP) that I've freed up about 90 GB of space. I'd like to make an image of my /home folder on the basement computer, wipe my main HDD, reinstall, and restore the /home folder. Like I said, it's about 80 GB.

Second question for this post - what's the best way to back up the /home folder? I've tried Clonezilla, but it wasn't readily obvious, even after reading the how-tos (yes, I'm an idiot). Other ideas?

By the way, this came about after I hooked up a card reader and dvd drive to my computer. It gave me an Error 21 and wouldn't boot up. I isolated everything, down to my original setup, and the error persisted. That's why I'd like to do the clean install.

---

### Post by Miljet on 2009-09-29
This might give you a starting point. It doesn't really discuss mounting network drives, but does give explicit instructions for backing up to network drives using rsync.

---

### Post by mikeyphi on 2009-09-29
If you think you have a Grub issue - I suggest you burn a copy of Supergrub to sort the problem.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by eeeek on 2009-10-08
By trial and error, I think I learned something about Grsync. 

I found out that Grsync won't see shared folders on a network drive that aren't in the c:/ directory (it's a windows drive).

I had the My Documents folder shared and Grsync couldn't see that folder. But then I put a shared folder in the C: directory, it recognized that. I guess you could say I found this out by accident - quite a key piece of info for me at the moment.

I am still working on backing up my data before the reinstall. No matter what the boot problem is, I am going to get a full backup before trying anything.

---

