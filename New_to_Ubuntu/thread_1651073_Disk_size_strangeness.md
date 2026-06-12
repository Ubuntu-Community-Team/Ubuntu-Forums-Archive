---
title: "Disk size strangeness"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by anthonye81 on 2010-12-22
I'm inexperienced with Linux and currently using an Ubuntu 10.10 live CD to back up some important folders from a Windows hard drive that I can't boot into at the moment.

The problem is how Ubuntu sees the disk and folder sizes. The disk is a single partition FAT32 160GB. Right-clicking on the volume and selecting properties tells me that the total capacity is indeed 147 GB, but the contents are more than 2 TB.

I'm trying to back up a few folders to a small-ish drive and Ubuntu warns me that there isn't enough space on the destination drive, and if I proceed regardless then it will be difficult to figure out which files have been copied across and which haven't.

Apologies if this matter has been covered elsewhere but I haven't found anything that answers this specifically.

---

### Post by corncob on 2010-12-22
> **anthonye81 said:**
> I'm inexperienced with Linux and currently using an Ubuntu 10.10 live CD to back up some important folders from a Windows hard drive that I can't boot into at the moment.

The problem is how Ubuntu sees the disk and folder sizes. The disk is a single partition FAT32 160GB. Right-clicking on the volume and selecting properties tells me that the total capacity is indeed 147 GB, but the contents are more than 2 TB.

I'm trying to back up a few folders to a small-ish drive and Ubuntu warns me that there isn't enough space on the destination drive, and if I proceed regardless then it will be difficult to figure out which files have been copied across and which haven't.

Apologies if this matter has been covered elsewhere but I haven't found anything that answers this specifically.

I get a pie chart when I do that so I don't understand how it could tell you that the contents are more than the total capacity.  I have a different situation though.  I have Ubuntu installed and Windows is on an NTFS partition on the same HD.  You might try GParted (System > Administration).

---

### Post by amjjawad on 2010-12-22
If you're backing up your data to an external HDD, try to give that external HDD a Label/Name so you could tell where to move your data.

---

### Post by anthonye81 on 2010-12-23
I get the pie chart too and that displays correct information. But just above it says 'Contents ... totalling 3.6TB' and still counting.

> **amjjawad said:**
> If you're backing up your data to an external HDD, try to give that external HDD a Label/Name so you could tell where to move your data.

Pointing the files to the destination disk isn't the problem, Ubuntu seems to think the source files/folders are several times bigger than they actually are. The source drive is 160GB and I'm trying to copy a few choice folders to an 80GB drive. However Ubuntu says these folders are about 900GB in size, and all the files on the source disk are more than 3TB.

I'll see if I can get a screen grab next time.

---

### Post by amjjawad on 2010-12-23
> **anthonye81 said:**
> I'll see if I can get a screen grab next time.

A screenshot will be nice.

Are you sure you're not on the wrong drive? do you have a drive with that size? I don't think so. I might be a bug but again, a screenshot is good idea.

---

