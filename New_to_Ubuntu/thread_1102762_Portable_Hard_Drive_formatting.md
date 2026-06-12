---
title: "Portable Hard Drive formatting"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-03-22
I recently got a portable hard drive, a Western Digital My Passport 500Gb. it came with software meant to be used in windows for automatic backup and an msdos format, i would like to format it to NTFS but i dont know how to do it. either from GUI or command line would be best. and I'm using Ubuntu 8.10. thanks!

---

### Post by HermanAB on 2009-03-22
If it was sold for use with Windows, then it is already formatted with NTFS.  So just hook it up - it should work.

Cheers,

Herman

---

### Post by egalvan on 2009-03-22
> **HermanAB said:**
> If it was sold for use with Windows, then it is already formatted with NTFS.
Herman

Believe it or don't, I've seen some of these external drives formatted as **FAT32**; yes, even jumbo sized 750GB. :)

Why anyone would use FAT32 on such a large drive, is beyond me.

ErnestG

Anyways, if you don't have Windows XP to do the job, then PartedMagic, or gparted, or a LiveCD will do the job.

Boot the LiveCD, make sure the drive is un-mounted, 
(if it IS mounted, right-click on the partition, then select "un-mount")
select the partition you need,
 erase it,
create a new one,
and format it as NTFS.

As easy as a piece of cake...

---

