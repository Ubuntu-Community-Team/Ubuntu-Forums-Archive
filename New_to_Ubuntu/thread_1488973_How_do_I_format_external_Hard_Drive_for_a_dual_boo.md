---
title: "How do I format external Hard Drive for a dual boot system?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by tykwondo on 2010-05-20
Hi Ubuntu community!

I have a laptop computer with a dual boot between Windows 7 and Lucid LTS. I want to format my Western Digital external hard drive so that both operating systems can read it. Right now, only Lucid can read the hard drive.

What steps to do need to take in order for both operating systems to read & access the external hard drive?

Thanks!

Ty

---

### Post by bodhi.zazen on 2010-05-20
Format it using any tool you like (Gparted will do), use NTFS or FAT (vfat) , both OS can read these two file systems.

---

### Post by sydbat on 2010-05-20
After backing up whatever data you have on the external drive, format it to NTFS so both Windows and Linux can read/write to it.

If you have not installed it yet, go to Synaptic (System > Tools > Synaptic) and look for ntfs-3g. This will allow you to read/write to an NTFS drive.

Also, if you have not installed the partitioner (gparted), do this from Synaptic as well.

EDIT - bodhi.zazen beat me to it. DOH!

---

### Post by tgalati4 on 2010-05-20
Or, leave the drive as it is and look for Windows 7 ext3 partition driver.

---

