---
title: "USB stick stuck in read-only mode."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by koffeinöverdos on 2009-04-15
I tried going into the properties and changing it to read and write but when I do that, it gives me an error saying i can't do that because its read only. I tried going into nautilus as root and everything, won't work.

It just suddenly started doing this today, does anyone have an idea?

---

### Post by Marlonsm on 2009-04-15
Same thing happened to me a few days ago.
I just backed up all data I had there and reformatted it.

I've also created a thread:
[http://ubuntuforums.org/showthread.php?t=1124722]("http://ubuntuforums.org/showthread.php?t=1124722")

---

### Post by eddietours on 2009-04-15
any chance you had that usb plug to windows

---

### Post by bodhi.zazen on 2009-04-15
Changing permissions depends on the file system.

If it is a FAT or NTFS system , you set permissions at the time of mounting.

What file system is it ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by koffeinöverdos on 2009-04-15
> **bodhi.zazen said:**
> Changing permissions depends on the file system.

If it is a FAT or NTFS system , you set permissions at the time of mounting.

What file system is it ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

Thank you very much for the guide, I had no idea about this. I'll start reading it, oh and my USB stick is fat32.

---

### Post by bodhi.zazen on 2009-04-15
Usually they auto-mount rw

But if there are errors in the file system or problems with the device (hardware issues) it will mount ro.

So you may want to check the disk integrity as well.

---

### Post by llamabr on 2009-04-15
Yes, when this was my issue, I backed up everything and formatted vfat or fat32, and it was fine.

Often the cause of this is not properly "unmounting" it (or whatever they call it) in windows.  You have to click a little thing in the lower right, saying release external disks, or whatever.

If you don't, often files will be only partially transfered, and it will corrupt the disk.

---

### Post by t0p on 2009-04-15
A short while ago, a usb stick of mine started mounting read-only all the time.  I reformatted it a few times, but it would soon become read-only again.  I took it back to where I bought it, and the guy said it was probably faulty physically and gave me a new one.

Maybe your stick is faulty too.

---

### Post by koffeinöverdos on 2009-04-16
> **t0p said:**
> A short while ago, a usb stick of mine started mounting read-only all the time.  I reformatted it a few times, but it would soon become read-only again.  I took it back to where I bought it, and the guy said it was probably faulty physically and gave me a new one.

Maybe your stick is faulty too.

Could be, it's a mysterious Chinese no-name stick. The price was great. lol

---

### Post by koffeinöverdos on 2009-04-16
> **llamabr said:**
> Yes, when this was my issue, I backed up everything and formatted vfat or fat32, and it was fine.

Often the cause of this is not properly "unmounting" it (or whatever they call it) in windows.  You have to click a little thing in the lower right, saying release external disks, or whatever.

If you don't, often files will be only partially transfered, and it will corrupt the disk.

i think thats exactly what happened. I've had some half-files on my disk ever since i messed up a transfer.

edit: I backed up and then used gparted to format it and it seems to work. Thanks everyone for your help.

---

