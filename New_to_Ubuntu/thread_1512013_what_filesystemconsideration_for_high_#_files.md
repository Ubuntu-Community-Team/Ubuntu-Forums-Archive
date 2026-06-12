---
title: "what filesystem/consideration for high # files?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by zetharx on 2010-06-17
I am running a vsftpd service on my desktop, and I have 10 security cameras uploading an image each every 15 seconds.  That is **40 images** each minute.  Each image size is roughly 150KB.

I want a record of 30 days, so that is 4x60x24x30= 172800 files in a single directory and x10 = 1.7 million files for all ten cameras.

Given these requirements, what considerations do I need to have to make sure that I am not breaking anything?  Is this too much load on my SATA HDD?  Could it die prematurely?  Which files system will handle this enormous list the best?  Please, any suggestions are encouraged.

---

### Post by insane_alien on 2010-06-17
259 200 000 kB in total then.

thats only ~260 GB.

thats not a whole lot of data considering. essentially any filesystem will handle this, even FAT32.

the harddrive should also easily be able to handle it without failing, although if it is an essential system you may want to set up a RAID1(use drives from different batches or even manufacturers to eliminate the chance of a construction fault causing htem to go bust in quick succession(unlikely)) or least make backups every now and then.

---

### Post by NightwishFan on 2010-06-17
I use ext4, though perhaps jfs or xfs may be better suited to a non-interactive workload. I say give jfs a try.

---

### Post by insane_alien on 2010-06-17
> **NightwishFan said:**
> I use ext4, though perhaps jfs or xfs may be better suited to a non-interactive workload. I say give jfs a try.

why? it only has to deal with a 150kB write and delete(the old file's going out of date) every 1.5s. this is hardly a taxing task. 

if it had to capture video from all of the cameras then there might be a point in picking a specialised filesystem but considering the very low demand on the hardware and software nothing is really going to have an impact on it.

---

### Post by NightwishFan on 2010-06-17
They are not specialized, its just that using them may be to an advantage or not. Depends on the workload. JFS is known to be light on cpu.

---

### Post by insane_alien on 2010-06-17
but we know the workload, its extremely light. practically idling, even if its an ancient computer.

---

### Post by NightwishFan on 2010-06-17
I agree with the backups though if you need to archive the images. I would use date sorted data DVDs.

---

### Post by srs5694 on 2010-06-17
ReiserFS is known for efficient handling of many small files, enabling it to pack more files into a given amount of space than is true for most other filesystems. That said, as insane_alien says, the total space required is about 260GB. If you've got a drive that's significantly larger than this (say, 500GB or more), ReiserFS's space efficiency might not be very important. OTOH, if you're trying to do this on a drive that's more like 350GB in size, that could be tight enough that ReiserFS will prove beneficial.

---

### Post by psusi on 2010-06-17
I believe ReiserFS is unmaintained these days and the original author is in prison for murdering his wife.  It also has several known deficiencies, so I would highly recommend against using it.  Besides, it's idea of small fies are on the order of 150 bytes, not 150k.

The workload described will be just fine on ext3/4.  And EXT has been around and well tested a lot longer than JFS.

---

### Post by srs5694 on 2010-06-18
File allocation on any filesystem is done in terms of the filesystem's block size, which is usually somewhere between 512 bytes and a few KiB (4 KiB is common). Assuming a random file size, the wasted disk space is, statistically speaking, half the allocation block size, so for a filesystem with an allocation block size of 4 KiB, each file will waste about 2 KiB, or about 1.3% if the filesystem is filled with ~150 KiB files. This works out to about 340 MiB for the case under consideration.

The advantage of ReiserFS is that it does rather aggressive "tail packing" -- stroring the small bits at the ends of several files together to waste less disk space. Thus, instead of losing 1.3% in this situation, you might lose a fraction of 1%. (I don't know the exact value.) I'm guessing you'd recover between 100 MiB and 300 MiB of disk space by using ReiserFS in the OP's case. Whether this improvement is important depends on the specific circumstances, of course.

As to the claims of ReiserFS being deficient and unmaintained, I haven't had problems with it in a decade or so of use. I have seen allegations of ReiserFS problems, but never any specifics. ReiserFS is part of the mainline kernel and has not been deprecated, so even if it's not seeing a lot of active development, so what? It already works. Personally, I trust it more than I trust ext4fs, which is still new enough that there have been problem reports related to its new features not very long ago.

---

### Post by Zill on 2010-06-18
> **psusi said:**
> I believe ReiserFS is unmaintained these days and the original author is in prison for murdering his wife...
This is an interesting point but I do not believe Hans Reiser's personal life is particularly relevant to this discussion.  ReiserFS is, in my experience, a rock solid filesystem that "just works".  As such, on the basis that "if it ain't broke don't fix it", there is no real requirement to change it .

On the other hand, my experience with ext3 was less inspiring, so there may well have been good reason to produce ext4!

---

