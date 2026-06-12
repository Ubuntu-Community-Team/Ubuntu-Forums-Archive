---
title: "Remove Ubunto from XP Pro"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by SyOliven on 2010-03-08
I have installed 9.10 Desktop Edition on several computers, but I would like to remove it from one that is running XP Pro.  Where can I find instructions to remove it, or will the UBUNTU 9.10 CD from which it was installed remove as well as install.:P

---

### Post by oldfred on 2010-03-08
You need to restore a windows boot loader to the MBR. You can use gparted to resize the XP partition or use it to reformat the ubuntu partition(s) to NTFS and use as data partitions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by juanoleso on 2010-03-08
If you installed through Wubi, you can uninstall from the Add/Remove menu.  Otherwise, follow what oldfred said.

---

### Post by presence1960 on 2010-03-08
An alternative to oldfred's suggestion (either way will work):

***_If you did not install ubuntu via wubi_*** boot into ubuntu and open a terminal and run ```
sudo apt-get install lilo
```Ignore the warning, then in terminal run ```
sudo lilo -M /dev/sda mbr
```

Your MBR will be a windows MBR so you can now boot either the Ubuntu Live CD (or gparted Live CD) and use gparted to remove the ubuntu partitions. Or you can boot to windows and delete the ubuntu partitions using disk management utility.

Which ever method you use to get rid of the ubuntu partitions you can use windows disk management utility to merge the unallocated space to Windows or create new partition(s)

---

