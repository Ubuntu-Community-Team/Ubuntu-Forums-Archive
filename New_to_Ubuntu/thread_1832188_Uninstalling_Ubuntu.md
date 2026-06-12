---
title: "Uninstalling Ubuntu"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by JsCoolDart on 2011-08-24
I have a dual boot PC with Widnwos 7 and Ubuntu... I need to uninstall Ubuntu completely, how do i go about doing that?

---

### Post by Mark Phelps on 2011-08-24
Instructions depend on HOW you installed it.

If you installed via Wubi, you simply use Control Panel --> Programs and Features to remove it.

If you installed to a separate partition, you can remove that partition using Win7 Disk Management utility.  But, BEFORE you do that, you should use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that to restore the original Win7 MBR (presuming you have just one hard drive).

---

### Post by Rex Bouwense on 2011-08-24
If you have a true dual boot with Windows and Ubuntu installed side by side then I believe that you can uninstall ubuntu by inserting the CD that you used to install Ubuntu and booting from the CD.  Once it boots use gparted to delete the partition that Ubuntu is installed on.  This will not work if you used WUBI.  If that is the case you can uninstall using the add/remove tool in Windows.

---

### Post by SidebySide on 2011-08-24
Live Disk >> Delete Partition >> This [Link]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

---

### Post by Mark Phelps on 2011-08-24
You can use whichever tool you want to remove the Ubuntu partition(s) -- just, if you use GParted, do not use it to then resize your Win7 partition(s).  Use the Win7 Disk Management utility, instead.

---

### Post by JsCoolDart on 2011-08-29
thanks so much :D

---

