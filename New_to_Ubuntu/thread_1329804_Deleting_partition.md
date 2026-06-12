---
title: "Deleting partition"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-11-17
I have a question about deleting partition. Please read on before deciding on GParted! I have a laptop with a windows and ubuntu partition. However, I have another computer that runs solely ubuntu so I wanted to delete the ubuntu partition on the laptop so to give windows more space. I know that I can delete the partition with GParted but what I'm unsure of is how windows is going to be able to use up that space. How can I do this?

---

### Post by kansasnoob on 2009-11-17
What version of Windows?

---

### Post by 5mattyb5 on 2009-11-17
You can run Gparted from a live cd because the drive needs to be unmounted.  Simply delete the ubuntu partition and resize the windows partition, it is all point and click really.  That is prabably the best way to do it.

---

### Post by antmenj on 2009-11-17
This thread may be of interest.

[http://ubuntuforums.org/showthread.php?t=1329927]("http://ubuntuforums.org/showthread.php?t=1329927")

---

### Post by oldfred on 2009-11-18
kansasnoob's question is important. If it is XP gparted is fine for everything. If Vista or 7 you only use gparted to delete the linux partition and use the internal partition editor to expand the windows partition.
Make sure you install windows back to the MBR before you delete ubuntu or you will not be able to boot.

---

### Post by Poincare101 on 2009-11-18
Okay, is the following how I do it:
[http://www.linuxforums.org/forum/ubuntu-help/72847-how-go-back-windows-mono-partition.html](http://www.linuxforums.org/forum/ubuntu-help/72847-how-go-back-windows-mono-partition.html)

( i have XP )

---

### Post by oldfred on 2009-11-18
I think that is pretty much what we have said. With XP you can use Gparted to delete & resize partitions.

I would first use the XP disk to do the repair fixMBR and make sure you can boot windows directly before deleting the partition. Many other tools are available to fix XP MBR including supergrub, testdisk and many liveCDs set up for repair.

---

