---
title: "Defrag Windows partition from Ubuntu"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-09-04
Quick query - is it possible to defragment a Windows NTFS partition from Ubuntu in a dual boot system?

I've lost access to Windows due to some corruption in the registry so need to do it from within Ubuntu before resizing (shrinkink) the windows partition.

Any help appreciated.

---

### Post by Jazzy_Jeff on 2010-09-04
Sounds like your computer is rebelling on you for keeping Windows ):P. Just kidding but could not resist.

---

### Post by Rubi1200 on 2010-09-04
Sorry to say this, but Windows problems need to be addressed on Windows forums.

I wish you the best of luck finding a solution.

---

### Post by stmiller on 2010-09-04
You can use the program ntfsfix to try and repair that windows partition. It's no miracle worker, but it's pretty much like chkdsk.

```

sudo apt-get install ntfsprogs

```

```

ntfsfix -fv /dev/ntfsdevicename

```

---

### Post by Gone fishing on 2010-09-04
I don't think there is a ntfs defrag tool. So I think you only have a few choices.

Borrow a Windows install CD and use that to defrag the partition apparently it is possible to make a live Windows CD and use that to defrag [http://www.howtohaven.com/system/live-windows-rescue-cd.shtml](http://www.howtohaven.com/system/live-windows-rescue-cd.shtml)

Copy the files off the partition delete the partition and then remake it.

---

### Post by sandyd on 2010-09-04
> **aquascrotum said:**
> Quick query - is it possible to defragment a Windows NTFS partition from Ubuntu in a dual boot system?

I've lost access to Windows due to some corruption in the registry so need to do it from within Ubuntu before resizing (shrinkink) the windows partition.

Any help appreciated.
In short, no.
Long version: Its possible to do this, but you will need to repair the windows partition first, before the defragmenter will run.

You can use chkdsk /f C: from a windows CD to do this and see if it will fix the corruption and allow windows to boot.

---

### Post by Mark Phelps on 2010-09-05
> **aquascrotum said:**
> Quick query - is it possible to defragment a Windows NTFS partition from Ubuntu in a dual boot system?

I've lost access to Windows due to some corruption in the registry so need to do it from within Ubuntu before resizing (shrinkink) the windows partition.

Any help appreciated.

If the registry is indeed corrupted, ANYTHING you do to the partition, apart from repairing it -- with CHKDSK, NOT with ntfsfix -- is almost certainly going to make matters a lot worse, not better.

Also, once you DO get it working, do NOT use GParted or the Ubuntu installer to shrink the MS Windows partition.  If you do that, you're likely to be back here with partition corruption -- again.

---

### Post by Sef on 2010-09-05
> Also, once you DO get it working, do NOT use GParted or the Ubuntu installer to shrink the MS Windows partition. If you do that, you're likely to be back here with partition corruption -- again.

You can use GParted to shrink the Windows Vista or 7 parition, but you will have to **reinstall** Windows again. (That's due to a Windows feature.)

---

### Post by jeight on 2010-09-05
There is no problem using the installer or gparted to shrink the volume, but you have to make sure windows is completely fragmented. That means using a commercial defrag program.  Some, like Perfect Disk, have free trials you can use.

As far as registy problems... If you know what the problem is you should be able to mount windows from your Linux partition.  It might be fixable.

---

