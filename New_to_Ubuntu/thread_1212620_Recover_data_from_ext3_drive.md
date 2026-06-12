---
title: "Recover data from ext3 drive"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by prenger745 on 2009-07-13
Ok.  I had an Ubuntu computer with 2 hard drives.  One was just an 80gb drive for file storage.  I am in the process of rebuilding the Ubuntu box but in the meantime I would like to retrieve data from the 80gb storage drive.

My bios recognizes the drive on boot, but once Windows XP loads, it doesn't show any kind of drive connected on Primary Slave position.  Is that normal?  What would be the best way to retrieve this data?

Thanks,
Dan

---

### Post by nhasian on 2009-07-13
regardless of wether or not windows can access the type of filesystem the partition may be using, it should at least show up in the disk manager.

anyway, you can access the drive by booting into your ubuntu partition, or if you dont have ubuntu installed you can boot from a LiveCD and then have access to all the drives.

if your volume is damaged you can try to recover the files using the tools PhotoRec & TestDisk

---

### Post by Zero++ on 2009-07-13
Dan,
Even though Linux will see a NTFS (XP drive) Windows doesn't get along so well with Linux. If you want to retrieve the data I would use the Live CD feature on the Ubuntu CD and boot into Ubuntu. Once the OS loads it should be able to detect both your 80 Gig Linux drive and your XP drive. Now just transfer the files you need from Linux drive to XP drive and you should be good to go. Just shut down, remove the CD from your ROM and you should boot back into XP like normal

Hope this helps,
Erik

---

### Post by raymondh on 2009-07-13
+1 on using the liveCD.

---

