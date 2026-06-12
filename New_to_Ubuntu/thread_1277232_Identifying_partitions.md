---
title: "Identifying partitions"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by joe2005 on 2009-09-28
I have a triple boot machine with XP on first hard disk and Windows seven and ubuntu 9.04 on second hard disk.While I am somewhat familiar with Windows Ubuntu is new to me and trying learn.Hence I have a lot of questions.Here is one.While I am on ubuntu other partitions are shown as 39 gb media,new volume,new volume etc.It is very difficult to open a file on other partitions.Is there a way to identify those partitions or have I done wrong install of ubuntu?

---

### Post by Bucky Ball on 2009-09-28
If they are NTFS partition open Synaptic Package Manager (System->Admin), search for and install ntfs-3g and ntfs-config. The second of these gives you a GUI that will identify any and all NTFS partitions in (or out of) the box and ask if you want them mounted at boot.

---

### Post by joe2005 on 2009-09-28
thanks.INstalled ntfs3-g and ntfs config When I ticked one new volume and applied I get an error occurred.I think I need still some more advice

---

### Post by Bartender on 2009-09-28
joe -
Boot into XP, then make sure to get out the proper way.  Start>Turn off Computer>Turn off.  Do the same thing with 7.  Boot back into Ubuntu.  The other disks should show up under "Computer" in Places, and you should be able to access them.
I've had no problems accessing Windows-formatted (FAT or NTFS) partitions in the last year or two with Ubuntu.  Maybe there are quirks with some motherboard chipsets, or some other odd hardware idiosyncrasies?

---

### Post by kambrik on 2009-09-28
fdisk -l from the terminal to see list of drives and partitions
fdisk -l /dev/hda to see partitions for that drive

[http://www.compuhowto.com/linux/ubuntu/linux-fdisk/]("http://www.compuhowto.com/linux/ubuntu/linux-fdisk/")

---

