---
title: "is there a windows removal tool?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by snooty29 on 2009-05-05
if someone installed windows on my mini laptop and then restored my factory settings with ububtu will it remove windows or dose anyone have a windows removal tool? my problem is that i have no space to download anything. i only have 5 pictures on here and i know it holds way more than that. my disk usage analyzer says its 97.2% full. someone please help.:KS

---

### Post by TheNosh on 2009-05-05
how big is your hard drive. more importantly, how big is your ubuntu partition?

---

### Post by pastalavista on 2009-05-05
You can remove the Windows partition with the Ubuntu Live CD. Boot from it and go to System > Administration > Partition Editor (gparted). It will show all your partitions. Delete the ones with NTFS file system. When it is deleted, expand the Ubuntu partition closest to it to fill the unallocated space. Then reboot.

---

### Post by snooty29 on 2009-05-05
the only ubuntu disk i have is the recovery media. how do i find the ubuntu partition?

---

### Post by laithbsoul on 2009-05-05
download a copy of Jaunty Jackalope or what ever ubuntu distro and install it over both

---

### Post by stretch427 on 2009-05-05
Than if you have a burner and a cd just create a live CD, or just use Gparted and make a disk of that. I find it very useful quite often. 
or boot off live USB

---

### Post by snooty29 on 2009-05-05
i am very new to this program sorry im so used to windows that i cant figure out how to do anything on here. i dont understand where i go to find the ubuntu partition. i did however look at my system monitor i have 2 filesystems that r exactly the same. one has all the folders in them the other has no folders. exp.    /dev/sda2      /        ext3     3.5 GiB 939.5 MiB 760.6 Mib 2.1GiB       77%

                   gvfs-fuse-daemon /home/cortney/.gvfs    fuse.gvfs-fuse-daemon 3.5 GiB 939.5 MiB  760.6 MiB    2.1 GiB  77%

---

### Post by snooty29 on 2009-05-05
thank u soo much i found the partition editor and fixed the problem!

---

### Post by stretch427 on 2009-05-06
Glad to be of any help!

---

