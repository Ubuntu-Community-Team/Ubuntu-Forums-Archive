---
title: "installing Ubuntu 10.10 on sdb"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by larrypg on 2011-04-28
Hello all,

I am going to install Ubuntu 10.10 on sdb.  WinXP is on sda.  I can not shift the boot order of the hd's in the bios.  Will grub be installed to the MBR of sda or sdb?  If sda is there anything I need to do to make sure that WinXP boots?

I also have some bad sectors on sdb.  Will the install check for bad sectors and not write to those or should fsck or something be run before the install.  By the way I have already set up / , /home, /swap before installing via the Livecd and gparted.  

Thanks for any help

---

### Post by Paqman on 2011-04-28
> **larrypg said:**
> Will grub be installed to the MBR of sda or sdb? 

By default sda, but you could install it to sdb if you wanted.


> If sda is there anything I need to do to make sure that WinXP boots?

Nope.

> 
I also have some bad sectors on sdb.  Will the install check for bad sectors and not write to those or should fsck or something be run before the install.

Bad sectors are normally handled by the drive itself, not the OS or filesystem. If you drive's SMART data is showing them as reallocated sectors then you've got nothing much to worry about. A lot of perfectly healthy drives will show a couple of bad sectors, it's just normal wear and tear. How many is "some bad sectors"?

---

### Post by larrypg on 2011-04-28
Hello,
Well it has around 1100KB of bad sectors on a 40G drive which is why I was wondering if fsck or some other program can flag the bad sectors so that when I install 10.10 it will not write to those blocks.  

As to the other question is it safest to add grub to sda or sdb to make it harder for things to not get a problem and then not be able to boot.

---

### Post by oldfred on 2011-04-28
If you cannot change boot order in BIOS as you have an old system that only boots from the primary master, you have to install grub's boot loader to sda as the primary master. Windows will not boot Ubuntu, but grub will give you the choice. I would always install it to sdb also, but that would then only be used if you ever plugged drive in as primary master.

Do not know how many errors are a problem but I would not rely on this drive for anything important.  And if you have problems, you should blame drive first.

---

### Post by Paqman on 2011-04-29
> **larrypg said:**
> Hello,
Well it has around 1100KB of bad sectors on a 40G drive which is why I was wondering if fsck or some other program can flag the bad sectors so that when I install 10.10 it will not write to those blocks.  


How many _actual_ bad sectors does the SMART data say it has? Normally they're expressed as a simple number, not in KB. If you have 1100 bad sectors, you have a problem.

The drive itself takes care of bad sectors, without needing anything to prompt it to do so. When bad sectors are identified they are put into the "pending reallocation" category in SMART, the drive then does its housekeeping and marks them as "reallocated bad sectors" (or similar). The drive will no longer try to write to them after this.

---

### Post by larrypg on 2011-05-09
hello all,
It has been a week or so since the last post.  It turns out to be 28 bad sectors from SMART on a 40 GB drive.  I am going to mark this as solved so I can start another topic...sort of the same but not exactly.

---

