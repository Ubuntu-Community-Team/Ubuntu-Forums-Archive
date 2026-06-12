---
title: "Can't mount usb flash drive. Also can't read/write to it nor can I format it! Need H"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Ubunser on 2010-09-09
Actually, the problem is perfectly put in the question. One thing to note is that before this happened I used it to install FreeBSD on laptop. So it contains a FreeBSD image and is still bootable - I just checked.

---

### Post by jtarin on 2010-09-09
If you have access to a Windows computer [here is one utility]("http://files.extremeoverclocking.com/file.php?f=197") that will return your flash drive to its original state. It works on all but the occasional odd-ball drive.
[And another.]("http://hddguru.com/software/2006.04.12-HDD-Low-Level-Format-Tool/")

---

### Post by Gone fishing on 2010-09-09
If its a FreeBSD bootable then it probably uses UFS file-system which Linux can't read. So you could use gparted to re-partition to ext3/4 ntfs or whatever.

If gparted isn't installed sudo apt-get install gparted

---

### Post by Ubunser on 2010-09-09
> **jtarin said:**
> If you have access to a Windows computer [here is one utility]("http://files.extremeoverclocking.com/file.php?f=197") that will return your flash drive to its original state. It works on all but the occasional odd-ball drive.
[And another.]("http://hddguru.com/software/2006.04.12-HDD-Low-Level-Format-Tool/")
I do have Windows. I can multiboot to three different systems, but I don't turn to Windows for help in purpose, cause I want to be able to settle problems independently on Linux.

---

### Post by Ubunser on 2010-09-09
> **Gone fishing said:**
> If its a FreeBSD bootable then it probably uses UFS file-system which Linux can't read. So you could use gparted to re-partition to ext3/4 ntfs or whatever.

If gparted isn't installed sudo apt-get install gparted

Thank you! I was playing around this issue in gparted, but I was looking to mount or format it. I was wrong. Thank you when I created a new partition f32 it works.

---

### Post by jtarin on 2010-09-09
> **Ubunser said:**
> I do have Windows. I can multiboot to three different systems, but I don't turn to Windows for help in purpose, cause I want to be able to settle problems independently on Linux.And I've just come from a post where the guy can't wait to get Linux off his computer and thought it would be easier for you and I didn't feel like taking three-four pages explaining how to do it in Linux.:p
Good for you.

---

