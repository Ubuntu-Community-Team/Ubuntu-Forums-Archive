---
title: "Cannot ac cess ubuntu ."
date: 2010-04-06
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-04-06
I had an ntfs partition along with my ubuntu partition(no windows).I was using it to keep data.I formatted the ntfs partition.While installation I selected this drive and windows installation was successful. Now I can not access my ubuntu partition.Whenever I start up my computer instead of showing the grub it takes me straight to windows 7.How do I access the linux partition.I had some really useful data on ubuntu partition which I haven't backed up.Is there a way out of this problem.

---

### Post by -humanaut- on 2010-04-06
You should be able to boot ubuntu from the harddrive using a livecd.

---

### Post by sisco311 on 2010-04-06
You have to reinstall the boot loader:
[uhelp]community/Grub2#Reinstalling%20GRUB%202[/uhelp]

---

### Post by pastalavista on 2010-04-06
> **peace.gangsta said:**
> I had an ntfs partition along with my ubuntu partition(no windows).I was using it to keep data.I formatted the ntfs partition.While installation I selected this drive and windows installation was successful. Now I can not access my ubuntu partition.Whenever I start up my computer instead of showing the grub it takes me straight to windows 7.How do I access the linux partition.I had some really useful data on ubuntu partition which I haven't backed up.Is there a way out of this problem.

You'll need to boot from the Ubuntu CD and reinstall grub. Instructions how-to here:
[http://ubuntuforums.org/showthread.php?p=9075999]("http://ubuntuforums.org/showthread.php?p=9075999")

---

