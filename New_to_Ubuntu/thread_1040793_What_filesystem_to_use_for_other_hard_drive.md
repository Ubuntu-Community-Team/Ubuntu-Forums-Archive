---
title: "What filesystem to use for other hard drive?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by gogogo111 on 2009-01-15
Hi, I'm using 8.10 64 bit. I have two hard drives, and I just came from Windows. I really like it so far, though there are some minor complaints I have.


However, I want to use the second hard drive as a place where I can store all my movies, music, etc...

In windows, I could just format both to ntfs and not worry about it, but in linux they use different file systems, so I'm a bit out of the loop. 

I have the first hard drive with ext3 and swap...how should I go about formatting the second one to just "store" things?

Thanks for reading! :P

---

### Post by BoardStupid on 2009-01-15
If you are only using Ubuntu then ext2 or ext3 will be fine. If you dual boot with Windows then FAT32 might be better, that way you can read/write from both OS's

---

### Post by crjackson on 2009-01-15
> **gogogo111 said:**
> Hi, I'm using 8.10 64 bit. I have two hard drives, and I just came from Windows. I really like it so far, though there are some minor complaints I have.


However, I want to use the second hard drive as a place where I can store all my movies, music, etc...

In windows, I could just format both to ntfs and not worry about it, but in linux they use different file systems, so I'm a bit out of the loop. 

I have the first hard drive with ext3 and swap...how should I go about formatting the second one to just "store" things?

Thanks for reading! :P

If you aren't going to try and access the drive from within windows too, I would format to ext3.

---

### Post by gogogo111 on 2009-01-15
Ok thanks guys, that seems simple enough. Anything else I should know?

---

### Post by handydan918 on 2009-01-15
> **gogogo111 said:**
> Ok thanks guys, that seems simple enough. Anything else I should know?

Yeah, just that you will need to edit /etc/fstab to automount that new drive (if you want it automounted...)

Just do a search on fstab and automounting and you should find plenty of threads.

---

### Post by hyper_ch on 2009-01-16
> **BoardStupid said:**
> If you dual boot with Windows then FAT32 might be better

forget fat32, it's ancient... besides with ntfs-3g you can easily write to a ntfs drive...

or you use ext2/3 drivers in windows to access the linux drives...

---

### Post by roscal on 2009-01-16
"or you use ext2/3 drivers in windows to access the linux drives..."

Really?
I didn't know this.
I have multiple fat32 drives, easily available for read/write, both in 
Kubuntu and Windows.

I also have a couple of ext/3 formatdrives. How can I access them in windows again?

You say there are drivers? For Windows?
Wow, I better boot it up one of these days to check this out, that would be great!

I realize I am getting off topic, but I think the fat32 is the route 
I would take. For easy dual recognition, it has always worked for me.

---

### Post by hyper_ch on 2009-01-16
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by roscal on 2009-01-16
> **hyper_ch said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

Ok, I didn't realize there were drivers for ext/3
If this works it will be awesome. Thanks!

---

### Post by Hallvor on 2009-01-16
+1 It is a much better solution to use the fs-driver since ext2/ext3 is an open and more advanced file system that works perfectly from windows.

---

### Post by vanadium on 2009-01-16
fat32 is still usefull because it guarantees most compatibility (readable/writable in Windows, Linux, Apple).

If no "ultimate" compatibility is required, more advanced file systems as ext3 or ntfs are recommended. ext3 is a free file system, ntfs a proprietary one, but that aspect will not determine your choice if you are still using Windows anyway.

Using ntfs will be easiest. No extra drivers needed in Ubuntu nor in Windows. Just make sure that the drive is properly disconnected each time, or Ubuntu will refuse to mount it at one time.

Using ext2 or ext3 requires a driver in Windows. An ext3 system will be used without journaling (i.e. as ext2) from within Windows. In your scenario, I'd prefer ntfs, but that ext2/ext3 fully supports linux permissions can be an additional advantage if it is important for you.

---

### Post by hyper_ch on 2009-01-16
extra drivers are need to write to ntfs in linux ;)

---

### Post by vanadium on 2009-01-16
> extra drivers are need to write to ntfs in linux

Ubuntu by default comes with full read/write support for ntfs. Most modern distributions will. If you are installing your custom linux system, you indeed will need to add ntfs-3g yourself if you want write support.

It might be semantics here: what is a "driver", what is an "extra driver". If it is something you need to install separately, then Ubuntu does not need an extra driver.

---

### Post by SamNSane on 2009-01-16
One really important point I didn't see mentioned concerns the very serious issue of FAT32's limitation on file sizes. In the OP there is mention of storage of "movies". If we're talking feature length movies, then FAT32 isn't going to cut it.

Besides, FAT32 is just a really awful file system by today's standards. It's okay for use on a flash drive or other small removable drive when you don't have file sizes bigger than 4 gigabytes, but it's more likely to allow loss of data than most other file system formats. I wouldn't have my only live copy of anything important on FAT32.

If you're using one of the more advanced journaling file systems from two operating systems, sure -- you may not be journaling when you're working from one of those operating systems. But at least you have journaling from the OS that uses the file system natively. And you have far more advanced recovery tools available to you.

---

### Post by albinootje on 2009-01-16
> **vanadium said:**
> fat32 is still usefull because it guarantees most compatibility (readable/writable in Windows, Linux, Apple).


I partially agree with this, but... with gnashing teeth.

First of all I would be surprised if it was completely impossible to use NTFS or ext2 formatted partitions in MacOSX (I've seen that it doesn't work by default on MacOSX laptops of my friends, but still).

And second of all, for data storage, the 4 Gb filesize limitation of FAT32 is something important to remember.
Try it, afair it will not even give you a warning, any files above 4 Gb filesize will just be cut off at 4 Gb filesize length.
Pretty bad if you're working with someone who does video editing, or when you need DVD iso images.

---

### Post by vanadium on 2009-01-16
fat32 is not the first choice, for sure. However, I do not know of another file system that has read/write support across Windows, Apple and Linux systems. If that compatibility is an issue, there is not much choice, but then, that is the only advantage of vfat. In as far as you need it.

@albinootje: very likely, it is technically feasible to support many different file systems on different platforms. However, I can only see that this did not happen currently. One of the main reasons might be the proprietary nature of the file systems of Microsoft and Apple. It are complex systems with no documentation publicly available.

---

### Post by albinootje on 2009-01-16
> **vanadium said:**
>  @albinootje: very likely, it is technically feasible to support many different file systems on different platforms. However, I can only see that this did not happen currently. One of the main reasons might be the proprietary nature of the file systems of Microsoft and Apple. It are complex systems with no documentation publicly available.

Well, I was in a rush when I posted my previous comment.

A quick search shows this now :
[http://www.macosxhints.com/article.php?story=20031031075607668](http://www.macosxhints.com/article.php?story=20031031075607668)
[http://www.macosxhints.com/article.php?story=20050521110452194&lsrc=osxh](http://www.macosxhints.com/article.php?story=20050521110452194&lsrc=osxh)
[http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html](http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html)

Sounds pretty good.

And, the following, for Mac-users for too much money in their wallets ;-)
[http://www.paragon-software.com/home/ntfs-mac/](http://www.paragon-software.com/home/ntfs-mac/)

---

### Post by crjackson on 2009-01-17
> **roscal said:**
> "or you use ext2/3 drivers in windows to access the linux drives..."

Really?
I didn't know this.
I have multiple fat32 drives, easily available for read/write, both in 
Kubuntu and Windows.

I also have a couple of ext/3 formatdrives. How can I access them in windows again?

You say there are drivers? For Windows?
Wow, I better boot it up one of these days to check this out, that would be great!

I realize I am getting off topic, but I think the fat32 is the route 
I would take. For easy dual recognition, it has always worked for me.

Couldn't disagree more. I have a similar setup and NTFS works perfectly. If you are going to have really big files (like I do) fat322 won't cut the mustard.

---

