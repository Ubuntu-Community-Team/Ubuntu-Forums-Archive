---
title: "freeing memory after uninstallation"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by ravikanth.vva on 2011-06-10
i uninstalled ubuntu using wubi....now i wanto reinstall it but my 500 gb hard disk is now showing only 389GB....do i have to  free space after uninstallation??


ok i got the problem....i installed the ubuntu seperately not throught wubi.....so i just uninstalled wubi.....
i dont know how to uninstall ubuntu because i installed it in the same partition as the windows.....can anyone help

---

### Post by coffeecat on 2011-06-13
Hi, I'm a little confused by what you're saying. You say you installed Ubuntu "separately not through Wubi", but then you go on to say that you installed it in the same partition as Windows. You can only install Ubuntu in the same partition as Windows if you use Wubi. So did you use Wubi, or did you install Ubuntu to its own partition?

There are three possibilities for what you describe. You installed Ubuntu to its own partition and the partition is still there, but unused. You installed Ubuntu using Wubi but it hasn't been properly uininstalled and the root.disk file is still there. Or - you have uninstalled a Wubi Ubuntu but that you've simply used up over 100GB in your C: drive.

Do two things. Open Windows' Disk Manager and post a screenshot so that we can see what your partition layout and sizes are like.

Open "Computer" and look in the C: drive. Is there a C:\ubuntu folder? If there is, look for a C:\ubuntu\disks\root.disk file. If it's there, how big is it? The root.disk file, if present, is your Ubuntu wubi virtual partition.

---

### Post by ravikanth.vva on 2011-07-29
i installed it in seperate partition but i used the default partitioning provided by ubuntu live cd.....due to which i thought it was installed in same partition.......problem solved....thanks

---

