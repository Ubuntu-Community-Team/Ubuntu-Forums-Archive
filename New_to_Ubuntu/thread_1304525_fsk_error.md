---
title: "fsk error"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Phil Hansen on 2009-10-29
I have added a extra hard disk for home and removed sdb2 from the first disk and then expanded sdb1 to use the whole disk.

On boot I get an error and the log is as follows:
Log of fsck -C3 -R -A -a 
Thu Oct 29 16:54:56 2009
fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Unable to resolve 'UUID=793de605-e17a-4c19-a929-4cdd54e70629' 
home_data: clean, 48228/12214272 files, 6251196/48839600 blocks
fsck died with exit status 8

Booted into recovery and ran the disk check but still get the same error.
Apart from that all works fine.

Help please to rid of this error message.
---
Thanks to SISCO311 problem is fixed.
Hope this [SOLVED] thing works in the title.

---

### Post by sisco311 on 2009-10-29
Did you remove the sdb2 entry from fstab?

What's the output of:
```
sudo blkid
cat /etc/fstab
```

---

### Post by Phil Hansen on 2009-10-29
> **sisco311 said:**
> Did you remove the sdb2 entry from fstab?

Thanks for that. Removed it and all OK.

---

### Post by sisco311 on 2009-10-29
> **Phil Hansen said:**
> Thanks for that. Removed it and all OK.

You are welcome! 

You can mark this thread as [solved] by selecting  **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

### Post by Phil Hansen on 2009-10-29
> **sisco311 said:**
> You can mark this thread as [solved] by selecting  **Mark this thread as solved** from the [COLOR=Red]Thread tools[/COLOR].

Missed that so tried my own method. Will know for next time.
Thanks for the help

---

