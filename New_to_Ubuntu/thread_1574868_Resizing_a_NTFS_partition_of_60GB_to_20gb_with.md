---
title: "Resizing a NTFS partition of 60GB to 20gb with"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-14
Hello,
I use the currently stable version of [http://partedmagic.com/](http://partedmagic.com/) working on a pendrive. 

The disk is nto used, it has only windows XP, and I would like to resize it to make space to install linux afterwards.

Gparted in this partedmagic does not allow resizing however :(

Best regards

---

### Post by CharlesA on 2010-09-14
Use a gparted livecd.

Also: Backup yer data before you mess with partitions.

---

### Post by honeybear on 2010-09-14
> **CharlesA said:**
> Use a gparted livecd.

Also: Backup yer data before you mess with partitions.

I already use one. it runs flawless done on pendrive with UNETBOOTIN. it rusn well, but it very seems taht gparted cannot resize ntfs.
> If you would like to use Parted Magic from a CD, first download this file and unzip it.
pmagic-5.5.iso.zip (md5sum: 731fbcedebe218cc200a032325f11d05)
Note: Other download locations are at the bottom of this page.


[https://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%205.5/pmagic-5.5.iso.zip/download](https://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%205.5/pmagic-5.5.iso.zip/download)

---

### Post by sandyd on 2010-09-14
> **honeybear said:**
> I already use one. it runs flawless done on pendrive with UNETBOOTIN. it rusn well, but it very seems taht gparted cannot resize ntfs.


[https://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%205.5/pmagic-5.5.iso.zip/download](https://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%205.5/pmagic-5.5.iso.zip/download)
try using the one from the ubuntu cd.

---

### Post by wilee-nilee on 2010-09-14
> **sandyd said:**
> try using the one from the ubuntu cd.

+1, and don't forget to reboot XP to make sure it's running okay before installing Ubuntu.

---

### Post by Faxanadu on 2010-09-15
I would recommend defragging in xp prior to resizing as well.

---

### Post by CharlesA on 2010-09-15
> **honeybear said:**
> I already use one. it runs flawless done on pendrive with UNETBOOTIN. it rusn well, but it very seems taht gparted cannot resize ntfs.

Hrm. I just resized an NTFS partition just fine in gparted. It takes a long time, but it works.

gparted-live-0.4.6-1.iso.

> **Faxanadu said:**
> I would recommend defragging in xp prior to resizing as well.

+1 to that. gparted will reallocate sectors and whatnot, but it's better to have everything is one (or two) chunks.

---

### Post by oldfred on 2010-09-15
Gparted will not work with a NTFS partition that needs chkdsk or is hibernate as flags are set. You may need to run chkdsk before you can resize it.
Windows needs 20-30% free space for NTFS to keep working or it slows down or stops.

---

### Post by CharlesA on 2010-09-15
> **oldfred said:**
> Gparted will not work with a NTFS partition that needs chkdsk or is hibernate as flags are set. You may need to run chkdsk before you can resize it.
Windows needs 20-30% free space for NTFS to keep working or it slows down or stops.

That makes sense. I don't think you can even clone a "dirty" volume.

---

### Post by honeybear on 2010-09-15
> **wilee-nilee said:**
> +1, and don't forget to reboot XP to make sure it's running okay before installing Ubuntu.

which iso or pendrive image woudl you recommend for such similar tricky resizing disk operation? 
(preferably a pendrive cuz there is no cdrom :( )

---

### Post by wilee-nilee on 2010-09-15
> **honeybear said:**
> which iso or pendrive image woudl you recommend for such similar tricky resizing disk operation? 
(preferably a pendrive cuz there is no cdrom :( )

In another thread oldfred mentions gpt partitioning, I think it references you. So I will defer to them as well as others in this thread who are more sure about this setup if it is the case.

If you have a regular set up, then just load the thumb with the OS you want to install and use gparted on the live cd. As mentioned if there are any flags on the ntfs partition it may need a chkdsk. You can right click XP in gparted and see any messages if you see a flag. Also mentioned in posts are having the XP defragged and leaving enough space in XP to run well. All good stuff.

If you don't know how to initiate a chkdsk let us know, it can be set up from the live XP or safe mode or a install cd to run at reboot.

---

