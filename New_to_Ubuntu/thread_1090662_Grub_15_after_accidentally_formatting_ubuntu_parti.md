---
title: "Grub 15 after accidentally formatting ubuntu partition"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-03-08
I'm having a very bad run with partitioning stuff, although this time was largely due to me not paying attention/gross neglect.

I was resizing my XP partition to free up more space for Ubuntu using GParted loading from a LiveCD. I managed to split off some space from XP but for some reason just couldn't get the free space combined to the Ubuntu partition. Played around with different formats for the 'unallocated partition', including ext2 and ext3 without success (why this is another thread I'll be starting later!). Some how, I managed to click on my Ubuntu partition instead of the empty space partition and formatted it to ext2.

Anyway it's done now, and fortunately I've backed up most of the critical stuff. When I restarted, I got grub 15.

What I basically want to do is to
1) Fix up grub so I can use my XP partition
2) Use XP to repartition
3) Reinstall Ubuntu
4) Get on with life
5) Never touch partitions again on this hard drive

Look forward to some help, thanks in advance.

---

### Post by whoop on 2009-03-08
So basically the only thing working on your machine now is xp, but you can't get there because grub is borked?

If the above is the case I would pop in the XP install cd and go to the repair option and run fixmbr.

---

### Post by HermanAB on 2009-03-08
Yup, use XP to fix the boot loader, then install Ubuntu all over again.

Note that when you resize partitions, you can grow a partition towards the end - you cannot grow a partition towards the front.

So if you start off with a single XP partition and carve off the last part of the disk for Ubuntu, you will have two partitions and all will be well.  If you later carve off some more space from the XP partition, then you cannot stich that onto the Ubuntu partition because Ubuntu resides at the end of the disk and cannot grow towards the front of the disk.  You have to give it a new partition name and put data on it, or you have to re-install Ubuntu as you are now doing.

Cheers,

Herman

---

### Post by paulchinnz on 2009-03-08
Thanks, will give it a go when get home. 

Not being able to grow backwards seems a bit odd ... is there anything besides Gparted that does the job of growing backwards by stitching it on and moving the data bit of the partition backwards in one go without having to do it manually?

---

### Post by paulchinnz on 2009-03-08
Thanks fixmbr worked.

Started booting XP but CHKDSK found that the volume was dirty in an effort to fix file 15944, which I'm guessing is the last file on the XP partition, it's got stuck "Deleting an index entry from index $O of file 15944" (for what seemed like a million times) before rebooting and there was Windows.

---

