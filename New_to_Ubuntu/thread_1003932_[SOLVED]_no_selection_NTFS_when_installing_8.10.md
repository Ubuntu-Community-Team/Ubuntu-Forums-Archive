---
title: "[SOLVED] no selection NTFS when installing 8.10 ?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by cliffm on 2008-12-06
Just installed 8.10 and wanted a NTFS partition. I did not see a selection for this there were several other selections, should I have used one of these?
Thanks for the help in advance
Cliffm

---

### Post by MarblePanther on 2008-12-06
ntfs is de facto for a windows user.

In linux world, the de facto (for the moment) is ext3.

You most likely have that as default--you'll be fine ;)

edit: NTFS is licensed by Microsoft, though there is an opensource version in development  (ntfs-3g)

---

### Post by mickeelm on 2008-12-06
> **cliffm said:**
> Just installed 8.10 and wanted a NTFS partition. I did not see a selection for this there were several other selections, should I have used one of these?
Thanks for the help in advance
Cliffm

If you want an NTFS partition that is possible, but there isn't really a reason for it if you are not going to dual boot with Windows and want to read from that partition from within Windows. If you are running only Ubuntu on one partition (or simply just using Ubuntu, regardless number of partitions) ext3 which is default is no problem.

---

### Post by cliffm on 2008-12-06
Thanks for the response. For awhile I will need to dual boot with XP. Will it load in ext3? I thought I needed NTFS?

---

### Post by mickeelm on 2008-12-06
> **cliffm said:**
> Thanks for the response. For awhile I will need to dual boot with XP. Will it load in ext3? I thought I needed NTFS?

You will have to have two partitions, at least. One for Windows (NTFS) and one for Ubuntu (ext3, not sure if you can pick other options but I think so).

So, Win XP will not load in ext3, but that is not a problem because you will have them on two different partitions.

If you want to have another partition (for music, videos etc) you could pick NTFS and it will be easily accessible from both Ubuntu and Win XP.

---

### Post by MarblePanther on 2008-12-06
Windows will use NTFS for its partition when you install it


I advise you to download supergrubdisk if you are planning on installing windows after linux.  You will need it because windows will take over your MBR and you wont be able to boot linux.  Supergrubdisk will allow you to reinstall grub after installing windows.

Installing windows first is always a better idea.

Also, supergrubdisk you burn to a cd and boot

---

### Post by scorp123 on 2008-12-06
> **cliffm said:**
> Just installed 8.10 and wanted a NTFS partition. NTFS is a proprietary Microsoft technology and "closed source", e.g. it's precise inner workings are treated as "trade secret" and not known to the outside world. There are various projects that have reverse-engineered the inner workings of NTFS such as the "ntfs-3g" project ... but while that software is "good enough" and "OK" for casually reading and writing to NTFS disks (e.g. to exchange data) it is definitely unfit for a full Linux OS installation: too slow (all operations have to go through "user space" instead of "kernel space" which would be way faster), and it doesn't have various features that a UNIX-like OS such as Linux would expect.

Windows can read Ext3 partitions with add-on software, e.g. with this one:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

